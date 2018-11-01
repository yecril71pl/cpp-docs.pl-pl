---
title: Konwertowanie danych nieobsługiwanych przez dostawcę
ms.date: 11/04/2016
helpviewer_keywords:
- OLE DB provider templates, unsupported data types
ms.assetid: f495e50f-530a-4fab-ab54-e0c359785845
ms.openlocfilehash: a53781f71a55dfb07dc996e5e25644d9337e4c63
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50473444"
---
# <a name="converting-data-not-supported-by-the-provider"></a>Konwertowanie danych nieobsługiwanych przez dostawcę

Gdy użytkownik zażąda typu danych, która nie jest obsługiwana przez dostawcę, szablonów dostawców OLE DB kod `IRowsetImpl::GetData` wywołuje Msdadc.dll można przekonwertować na typ danych.

W przypadku zaimplementowania interfejsu, takich jak `IRowsetChange` który wymaga konwersji danych, można wywołać Msdaenum.dll, aby wykonać konwersję. Użyj `GetData`zdefiniowaną w Atldb.h jako przykład.

## <a name="see-also"></a>Zobacz też

[Praca z szablonami dostawców OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)