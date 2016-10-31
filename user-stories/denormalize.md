---
title: Denormalize
section: user-stories
as-a: User
want: a simple tool that will denormalize any normalized files in my Data Package
so-that: I can load my data into tools that don’t support multiple tables
---

## User Story

*As a {{ page.as-a }}, I want {{ page.want }} so that {{ page.so-that }}*

As an example, I have two files: `participants.csv` and `programs.csv`
that I have Data Packaged.  In the `datapackage.json` (see
[below](#original-data-package)), I have defined a
[foreign key](http://specs.dataatwork.org/json-table-schema/#foreign-keys)
relationship between these two resources.

`# participants.csv`

| ParticipanID | ProgramID |
|---|---|
| 1234 | 4321 |

`# programs.csv`

| ID | Name |
|---|---|
| 1234 | Ruby Bootcamp |

[DPM](https://github.com/okfn/dpm) is a command line tool for working
with Training Data Packages.  At the simplest level, it would be ideal for `dpm
merge mydatapackage` to generate the following CSV data on standard
output.  This would be roughly equivalent to the output of the
following `csvsql` (see
[csvkit](http://csvkit.readthedocs.org/en/latest/scripts/csvsql.html))
command:

```
csvsql --query 'SELECT ParticipantID,ProgramID,Name AS program_Name            \\
                FROM participants                                             \\
                INNER JOIN programs                                      \\ 
                ON participants.ProgramID=programs.ID'                       \\
participants.csv programs.csv 

```

| ParticipantID |  ProgramID | program_Name |
|---|---|---|
| 1234 | 4321 | Ruby Bootcamp |

Here are some options for the command:

- `--datapackage PATH` 

  Given that we are starting with a Data Package, we should also be
  able to generate a new Data Package at a given `PATH`.  All fields
  from the original Data Package should be carried over, but it should
  have no `foreignkeys` and should consist of only one resource.

## Original Data Package

`# datapackage.json`

```
{
  "name": "participant-program",
  "resources": [
    {
      "name": "participants",
      "path": "participants.csv",
      "schema": {
        "fields": [
          {
            "name": "ParticipantID",
            "type": "integer"
          },
          {
            "name": "ProgramID",
            "type": "integer"
          }
        ],
        "foreignKeys": [
          {
            "fields": "ProgramID",
            "reference": {
              "resource": "programs",
              "fields": "ID"
            }
          }
        ]
      }
    },
    {
      "name": "programs",
      "path": "programs.csv",
      "schema": {
        "fields": [
          {
            "name": "ID",
            "type": "integer"
          },
          {
            "name": "Name",
            "type": "string"
          }
        ]
      }
    }
  ]
}

```

## Reference

- [csv-join](https://github.com/maxogden/csv-join) by Max Ogden
- [csvjoin](http://csvkit.readthedocs.org/en/latest/scripts/csvjoin.html) by Christopher Groskopf
