---
title: 'Źródło danych: określanie schematu źródła danych (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC data sources [C++], schema
- schemas [C++], data sources
- data sources [C++], determining schema
ms.assetid: 17284acb-eb10-4f27-9944-ad1d973c0b05
ms.openlocfilehash: ed6500c5718cf90b39600b12659a3090fe9532ce
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50580784"
---
# <a name="data-source-determining-the-schema-of-the-data-source-odbc"></a>Źródło danych: określanie schematu źródła danych (ODBC)

Ten temat dotyczy klas MFC ODBC.

Do skonfigurowania elementów członkowskich danych w Twojej `CRecordset` obiektów, musisz znać schematu źródła danych, z którym chcesz się połączyć. Określanie schematu źródła danych polega na uzyskiwanie listę tabel w źródle danych, lista kolumn w każdej tabeli, typ danych w każdej kolumnie i istnienie żadnych indeksów.

## <a name="see-also"></a>Zobacz też

[Źródło danych (ODBC)](../../data/odbc/data-source-odbc.md)<br/>
[Źródło danych: zarządzanie połączeniami (ODBC)](../../data/odbc/data-source-managing-connections-odbc.md)