---
title: "Konwertowanie danych nieobsługiwanych przez dostawcę | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: OLE DB provider templates, unsupported data types
ms.assetid: f495e50f-530a-4fab-ab54-e0c359785845
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3dff3b8a7041c24f5becedb207b1aa9a9193afbf
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="converting-data-not-supported-by-the-provider"></a>Konwertowanie danych nieobsługiwanych przez dostawcę
Gdy klient żąda typu danych, która nie jest obsługiwana przez dostawcę, szablonów dostawców OLE DB kod `IRowsetImpl::GetData` wywołuje Msdadc.dll można przekonwertować na typ danych.  
  
 Jeśli implementuje interfejs, takich jak `IRowsetChange` który wymaga konwersji danych, należy wywołać Msdaenum.dll można wykonać konwersji. Użyj `GetData`zdefiniowanej w Atldb.h, na przykład.  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z szablonami dostawców OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)