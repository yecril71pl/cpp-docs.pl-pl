---
title: 'Źródło danych: Określanie schematu źródła danych (ODBC) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ODBC data sources [C++], schema
- schemas [C++], data sources
- data sources [C++], determining schema
ms.assetid: 17284acb-eb10-4f27-9944-ad1d973c0b05
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b5ba9789226e54c9607e85caaa5e8af3f157f02d
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50052641"
---
# <a name="data-source-determining-the-schema-of-the-data-source-odbc"></a>Źródło danych: określanie schematu źródła danych (ODBC)

Ten temat dotyczy klas MFC ODBC.

Do skonfigurowania elementów członkowskich danych w Twojej `CRecordset` obiektów, musisz znać schematu źródła danych, z którym chcesz się połączyć. Określanie schematu źródła danych polega na uzyskiwanie listę tabel w źródle danych, lista kolumn w każdej tabeli, typ danych w każdej kolumnie i istnienie żadnych indeksów.

## <a name="see-also"></a>Zobacz też

[Źródło danych (ODBC)](../../data/odbc/data-source-odbc.md)<br/>
[Źródło danych: zarządzanie połączeniami (ODBC)](../../data/odbc/data-source-managing-connections-odbc.md)