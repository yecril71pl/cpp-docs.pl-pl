---
title: Konwertowanie danych nieobsługiwanych przez dostawcę | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB provider templates, unsupported data types
ms.assetid: f495e50f-530a-4fab-ab54-e0c359785845
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: fa9fed1f7c779efc7104ec8138d618b85aeb2a33
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46081744"
---
# <a name="converting-data-not-supported-by-the-provider"></a>Konwertowanie danych nieobsługiwanych przez dostawcę

Gdy użytkownik zażąda typu danych, która nie jest obsługiwana przez dostawcę, szablonów dostawców OLE DB kod `IRowsetImpl::GetData` wywołuje Msdadc.dll można przekonwertować na typ danych.  
  
W przypadku zaimplementowania interfejsu, takich jak `IRowsetChange` który wymaga konwersji danych, można wywołać Msdaenum.dll, aby wykonać konwersję. Użyj `GetData`zdefiniowaną w Atldb.h jako przykład.  
  
## <a name="see-also"></a>Zobacz też  

[Praca z szablonami dostawców OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)