---
title: 'Źródło danych: Określanie schematu źródła danych (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC data sources [C++], schema
- schemas [C++], data sources
- data sources [C++], determining schema
ms.assetid: 17284acb-eb10-4f27-9944-ad1d973c0b05
ms.openlocfilehash: c419a3ac2d870e6a85675492ee6c9b726427a0e9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395979"
---
# <a name="data-source-determining-the-schema-of-the-data-source-odbc"></a>Źródło danych: Określanie schematu źródła danych (ODBC)

Ten temat dotyczy klas MFC ODBC.

Do skonfigurowania elementów członkowskich danych w Twojej `CRecordset` obiektów, musisz znać schematu źródła danych, z którym chcesz się połączyć. Określanie schematu źródła danych polega na uzyskiwanie listę tabel w źródle danych, lista kolumn w każdej tabeli, typ danych w każdej kolumnie i istnienie żadnych indeksów.

## <a name="see-also"></a>Zobacz także

[Źródło danych (ODBC)](../../data/odbc/data-source-odbc.md)<br/>
[Źródło danych: zarządzanie połączeniami (ODBC)](../../data/odbc/data-source-managing-connections-odbc.md)