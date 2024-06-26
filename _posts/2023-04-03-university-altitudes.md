---
layout: post
category: thoughts
title: The ultimate academic league table - How high is your university above sea level?
---

Prof. [Joanna Bryson](https://mastodon.social/@j2bryson) recently mentioned that Bath is [the highest university above sea level in the UK](https://mastodon.social/@j2bryson/110133731573164180). For some reason this suprised me, but my quick search for confirmation only found me endless league tables.

Thankfully, #OpenData came to the rescue!

First, JISC provides a portal covering [equipment owned by UK universities](https://data.ac.uk/) which handily provides a clean CSV file of the [address of every university in the UK](http://learning-provider.data.ac.uk/).

And second, [Get The Data](https://www.getthedata.com/open-postcode-elevation) provides not only a nice searchable index linking locations to altitude, but also lets you download a corresponding CSV file.

Loading both into Pandas dataframes let me quickly generate a list of all[^1] UK universities sorted by height above sea level. And I then discovered that Pandas now let's you [export direct to Markdown](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.to_markdown.html)! So one copy/paste[^2] and here we are:


| Learning Provider                                         | Town                 | altitude (m) |
| :-------------------------------------------------------- | :------------------- | :----------: |
| UNIVERSITY OF BATH (THE)                                  | BATH                 |     190      |
| UNIVERSITY OF KEELE                                       | NEWCASTLE            |     190      |
| NEWMAN UNIVERSITY                                         | BIRMINGHAM           |     190      |
| LEEDS TRINITY UNIVERSITY                                  | LEEDS                |     170      |
| UNIVERSITY OF WOLVERHAMPTON                               | WOLVERHAMPTON        |     160      |
| UNIVERSITY OF BIRMINGHAM                                  | BIRMINGHAM           |     140      |
| UNIVERSITY OF ST MARK & ST JOHN                           | PLYMOUTH             |     140      |
| UNIVERSITY COLLEGE BIRMINGHAM                             | BIRMINGHAM           |     140      |
| ROYAL AGRICULTURAL UNIVERSITY                             | Cirencester          |     130      |
| ASTON UNIVERSITY                                          | BIRMINGHAM           |     120      |
| UNIVERSITY OF BRADFORD                                    | BRADFORD             |     120      |
| STAFFORDSHIRE UNIVERSITY                                  | STOKE-ON-TRENT       |     120      |
| UNIVERSITY OF SHEFFIELD                                   | SHEFFIELD            |     120      |
| UNIVERSITY OF BEDFORDSHIRE                                | LUTON                |     110      |
| CRANFIELD UNIVERSITY                                      | BEDFORD              |     100      |
| OXFORD BROOKES UNIVERSITY                                 | OXFORD               |     100      |
| UNIVERSITY OF BOLTON                                      | BOLTON               |     100      |
| BIRMINGHAM CITY UNIVERSITY                                | BIRMINGHAM           |     100      |
| HERIOT-WATT UNIVERSITY                                    | CURRIE               |      90      |
| UNIVERSITY OF HERTFORDSHIRE                               | HATFIELD             |      90      |
| GLYNDWR UNIVERSITY                                        | WREXHAM              |      90      |
| MIDDLESEX UNIVERSITY                                      | LONDON               |      80      |
| COVENTRY UNIVERSITY                                       | COVENTRY             |      80      |
| UNIVERSITY FOR THE CREATIVE ARTS                          | FARNHAM              |      80      |
| THE UNIVERSITY OF BUCKINGHAM                              | BUCKINGHAM           |      80      |
| UNIVERSITY OF SOUTH WALES/PRIFYSGOL DE CYMRU              | PONTYPRIDD           |      80      |
| UNIVERSITY OF WARWICK                                     | COVENTRY             |      80      |
| UNIVERSITY OF DERBY                                       | DERBY                |      80      |
| UNIVERSITY OF LEICESTER                                   | LEICESTER            |      80      |
| LEEDS COLLEGE OF ART                                      | LEEDS                |      80      |
| SRUC                                                      | EDINBURGH            |      80      |
| UNIVERSITY OF LEEDS                                       | LEEDS                |      80      |
| UNIVERSITY OF EXETER                                      | EXETER               |      80      |
| UNIVERSITY OF HUDDERSFIELD                                | HUDDERSFIELD         |      80      |
| UNIVERSITY OF WINCHESTER                                  | WINCHESTER           |      70      |
| OPEN UNIVERSITY(THE)                                      | MILTON KEYNES        |      70      |
| UNIVERSITY OF READING                                     | READING              |      70      |
| BATH SPA UNIVERSITY                                       | BATH                 |      70      |
| UNIVERSITY OF SUSSEX                                      | BRIGHTON             |      70      |
| HARPER ADAMS UNIVERSITY                                   | Newport              |      70      |
| BUCKINGHAMSHIRE NEW UNIVERSITY                            | HIGH WYCOMBE         |      70      |
| UNIVERSITY OF THE WEST OF ENGLAND, BRISTOL                | BRISTOL              |      70      |
| UNIVERSITY OF EDINBURGH                                   | EDINBURGH            |      70      |
| UNIVERSITY OF BRISTOL                                     | BRISTOL              |      70      |
| EDINBURGH NAPIER UNIVERSITY                               | EDINBURGH            |      70      |
| LOUGHBOROUGH UNIVERSITY                                   | LOUGHBOROUGH         |      60      |
| UNIVERSITY OF DURHAM                                      | DURHAM               |      60      |
| UNIVERSITY OF NORTHAMPTON,THE                             | NORTHAMPTON          |      60      |
| UNIVERSITY OF OXFORD                                      | OXFORD               |      60      |
| THE ROYAL CENTRAL SCHOOL OF SPEECH AND DRAMA              | LONDON               |      60      |
| SHEFFIELD HALLAM UNIVERSITY                               | SHEFFIELD            |      60      |
| LIVERPOOL HOPE UNIVERSITY                                 | LIVERPOOL            |      60      |
| UNIVERSITY OF GLOUCESTERSHIRE                             | Cheltenham           |      60      |
| LEEDS METROPOLITAN UNIVERSITY                             | LEEDS                |      60      |
| SWANSEA METROPOLITAN UNIVERSITY                           | SWANSEA              |      60      |
| DE MONTFORT UNIVERSITY                                    | LEICESTER            |      60      |
| UNIVERSITY OF KENT                                        | CANTERBURY           |      60      |
| BISHOP GROSSETESTE UNIVERSITY                             | LINCOLN              |      60      |
| UNIVERSITY OF SURREY                                      | GUILDFORD            |      60      |
| EDGE HILL UNIVERSITY                                      | ORMSKIRK             |      60      |
| UNIVERSITY OF LANCASTER                                   | LANCASTER            |      60      |
| NEWCASTLE UNIVERSITY                                      | NEWCASTLE UPON TYNE  |      50      |
| BANGOR UNIVERSITY                                         | BANGOR               |      50      |
| BOURNEMOUTH UNIVERSITY                                    | POOLE                |      50      |
| ROYAL HOLLOWAY COLLEGE AND BEDFORD NEW COLLEGE            | EGHAM                |      50      |
| NOTTINGHAM TRENT UNIVERSITY                               | NOTTINGHAM           |      50      |
| ARTS UNIVERSITY BOURNEMOUTH, THE                          | POOLE                |      50      |
| NORTHERN SCHOOL OF CONTEMPORARY DANCE                     | LEEDS                |      50      |
| ROYAL NORTHERN COLLEGE OF MUSIC                           | MANCHESTER           |      40      |
| THE LIVERPOOL INSTITUTE FOR PERFORMING ARTS               | Liverpool            |      40      |
| UNIVERSITY OF SALFORD, THE                                | SALFORD              |      40      |
| UNIVERSITY OF BRIGHTON                                    | BRIGHTON             |      40      |
| UNIVERSITY OF SOUTHAMPTON                                 | SOUTHAMPTON          |      40      |
| FALMOUTH UNIVERSITY                                       | Falmouth             |      40      |
| LEEDS COLLEGE OF MUSIC                                    | LEEDS                |      40      |
| GLASGOW CALEDONIAN UNIVERSITY                             | GLASGOW              |      40      |
| BRUNEL UNIVERSITY                                         | UXBRIDGE             |      40      |
| UNIVERSITY OF WALES: TRINITY SAINT DAVID                  | CARMARTHEN           |      40      |
| UNIVERSITY OF GLASGOW                                     | GLASGOW              |      40      |
| THE UNIVERSITY OF MANCHESTER                              | MANCHESTER           |      40      |
| PLYMOUTH UNIVERSITY                                       | PLYMOUTH             |      40      |
| NORTHUMBRIA UNIVERSITY NEWCASTLE                          | Newcastle Upon Tyne  |      40      |
| GLASGOW SCHOOL OF ART.                                    | GLASGOW              |      40      |
| LIVERPOOL JOHN MOORES UNIVERSITY                          | LIVERPOOL            |      30      |
| UNIVERSITY OF CENTRAL LANCASHIRE                          | PRESTON              |      30      |
| ROYAL CONSERVATOIRE OF SCOTLAND                           | GLASGOW              |      30      |
| UNIVERSITY OF NOTTINGHAM, THE                             | NOTTINGHAM           |      30      |
| LONDON BUSINESS SCHOOL                                    | LONDON               |      30      |
| UNIVERSITY OF WEST LONDON                                 | LONDON               |      30      |
| ROYAL ACADEMY OF MUSIC                                    | LONDON               |      30      |
| ANGLIA RUSKIN UNIVERSITY                                  | CHELMSFORD           |      30      |
| UNIVERSITY OF SUNDERLAND                                  | SUNDERLAND           |      30      |
| LONDON METROPOLITAN UNIVERSITY                            | LONDON               |      30      |
| ROEHAMPTON UNIVERSITY                                     | LONDON               |      30      |
| UNIVERSITY OF WORCESTER, THE                              | WORCESTER            |      30      |
| QUEEN MARGARET UNIVERSITY, EDINBURGH                      | MUSSELBURGH          |      30      |
| UNIVERSITY OF STIRLING                                    | STIRLING             |      30      |
| WRITTLE COLLEGE                                           | CHELMSFORD           |      30      |
| ROSE BRUFORD COLLEGE                                      | Sidcup               |      30      |
| MANCHESTER METROPOLITAN UNIVERSITY                        | MANCHESTER           |      30      |
| LONDON SCHOOL OF HYGIENE AND TROPICAL MEDICINE            | LONDON               |      20      |
| UNIVERSITY OF CHESTER                                     | CHESTER              |      20      |
| QUEEN MARY UNIVERSITY OF LONDON                           | LONDON               |      20      |
| UNIVERSITY COLLEGE LONDON                                 | LONDON               |      20      |
| THE ROBERT GORDON UNIVERSITY                              | ABERDEEN             |      20      |
| SCHOOL OF PHARMACY UNIVERSITY OF LONDON(THE)              | LONDON               |      20      |
| THE CITY UNIVERSITY                                       | LONDON               |      20      |
| CANTERBURY CHRIST CHURCH UNIVERSITY                       | CANTERBURY           |      20      |
| THE CONSERVATOIRE FOR DANCE AND DRAMA                     | LONDON               |      20      |
| YORK ST JOHN UNIVERSITY                                   | YORK                 |      20      |
| BIRKBECK COLLEGE                                          | LONDON               |      20      |
| UNIVERSITY OF LONDON                                      | LONDON               |      20      |
| GUILDHALL SCHOOL OF MUSIC & DRAMA                         | LONDON               |      20      |
| UNIVERSITY OF ABERTAY DUNDEE                              | DUNDEE               |      20      |
| UNIVERSITY OF ESSEX                                       | COLCHESTER           |      20      |
| UNIVERSITY OF THE ARTS, LONDON                            | LONDON               |      20      |
| SCHOOL OF ORIENTAL AND AFRICAN STUDIES                    | LONDON               |      20      |
| THE ROYAL VETERINARY COLLEGE                              | LONDON               |      20      |
| CARDIFF UNIVERSITY                                        | CARDIFF              |      20      |
| GOLDSMITHS' COLLEGE                                       | LONDON               |      20      |
| LONDON SCHOOL OF ECONOMICS & POLITICAL SCIENCE            | LONDON               |      20      |
| THE UNIVERSITY OF CUMBRIA                                 | CARLISLE             |      20      |
| ROYAL COLLEGE OF ART(THE)                                 | LONDON               |      20      |
| THE UNIVERSITY OF WESTMINSTER                             | LONDON               |      20      |
| UNIVERSITY OF ST ANDREWS                                  | ST. ANDREWS          |      20      |
| INSTITUTE OF EDUCATION, UNIVERSITY OF LONDON              | LONDON               |      20      |
| SWANSEA UNIVERSITY                                        | SWANSEA              |      20      |
| UNIVERSITY OF EAST ANGLIA                                 | NORWICH              |      20      |
| UNIVERSITY OF DUNDEE                                      | DUNDEE               |      20      |
| UNIVERSITY OF YORK                                        | YORK                 |      20      |
| THE UNIVERSITY OF CHICHESTER                              | CHICHESTER           |      20      |
| UNIVERSITY OF STRATHCLYDE                                 | GLASGOW              |      20      |
| SOUTHAMPTON SOLENT UNIVERSITY                             | SOUTHAMPTON          |      10      |
| COURTAULD INSTITUTE OF ART                                | LONDON               |      10      |
| UNIVERSITY OF CAMBRIDGE                                   | CAMBRIDGE            |      10      |
| CARDIFF METROPOLITAN UNIVERSITY                           | CARDIFF              |      10      |
| UNIVERSITY OF THE WEST OF SCOTLAND                        | PAISLEY              |      10      |
| UNIVERSITY OF LINCOLN                                     | LINCOLN              |      10      |
| IMPERIAL COLLEGE OF SCIENCE, TECHNOLOGY AND MEDICINE      | LONDON               |      10      |
| UNIVERSITY OF WALES PRIFYSGOL CYMRU                       | CARDIFF              |      10      |
| UNIVERSITY CAMPUS SUFFOLK LTD                             | IPSWICH              |      10      |
| LONDON SOUTH BANK UNIVERSITY                              | LONDON               |      10      |
| ROYAL WELSH COLLEGE OF MUSIC AND DRAMA LIMITED            | CARDIFF              |      10      |
| NORWICH UNIVERSITY OF THE ARTS                            | NORWICH              |      10      |
| INSTITUTE OF CANCER RESEARCH: ROYAL CANCER HOSPITAL (THE) | LONDON               |      10      |
| ROYAL COLLEGE OF MUSIC                                    | LONDON               |      10      |
| PRIFYSGOL ABERYSTWYTH                                     | ABERYSTWYTH          |      10      |
| KING'S COLLEGE LONDON                                     | LONDON               |      10      |
| UNIVERSITY OF ABERDEEN                                    | ABERDEEN             |      10      |
| UNIVERSITY OF EAST LONDON                                 | LONDON               |      10      |
| TEESSIDE UNIVERSITY                                       | MIDDLESBROUGH        |      10      |
| UNIVERSITY OF THE HIGHLANDS AND ISLANDS                   | Inverness            |      10      |
| UNIVERSITY OF PORTSMOUTH                                  | PORTSMOUTH           |      10      |
| TRINITY LABAN CONSERVATOIRE OF MUSIC AND DANCE LTD        | LONDON               |      10      |
| HEYTHROP COLLEGE                                          | LONDON               |      10      |
| KINGSTON UNIVERSITY                                       | KINGSTON UPON THAMES |      10      |
| ST MARY'S UNIVERSITY, TWICKENHAM                          | TWICKENHAM           |      10      |
| UNIVERSITY OF LIVERPOOL                                   | LIVERPOOL            |      10      |
| ST. GEORGE'S, UNIVERSITY OF LONDON                        | LONDON               |      10      |
| UNIVERSITY OF GREENWICH                                   | London               |      10      |
| RAVENSBOURNE                                              | LONDON               |      0       |
| UNIVERSITY OF HULL                                        | HULL                 |      0       |



<br>
<br>

[^1]: Almost all: the postcode file doesn't include Northern Ireland, so the table misses out four universities there. Belfast is c.3 metres above sea level.

[^2]: Almost just that: to render it in Github Pages markdown, I had to delete all the extra hyphen-filled lines I'd accidentally produced. But still. Not complicated.