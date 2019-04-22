---
title: Konwertowanie danych nieobsługiwanych przez dostawcę
ms.date: 10/29/2018
helpviewer_keywords:
- OLE DB provider templates, unsupported data types
ms.assetid: f495e50f-530a-4fab-ab54-e0c359785845
ms.openlocfilehash: e60f6cd4f7dca1ed3e176cabefc42f69946436a4
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59033842"
---
# <a name="converting-data-not-supported-by-the-provider"></a>Konwertowanie danych nieobsługiwanych przez dostawcę

Gdy użytkownik zażąda typu danych, która nie jest obsługiwana przez dostawcę, szablonów dostawców OLE DB kod `IRowsetImpl::GetData` wywołuje Msdadc.dll można przekonwertować na typ danych.

W przypadku zaimplementowania interfejsu, takich jak `IRowsetChange` który wymaga konwersji danych, można wywołać Msdaenum.dll, aby wykonać konwersję. Użyj `GetData`zdefiniowaną w Atldb.h jako przykład.

## <a name="see-also"></a>Zobacz także

[Praca z szablonami dostawców OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)