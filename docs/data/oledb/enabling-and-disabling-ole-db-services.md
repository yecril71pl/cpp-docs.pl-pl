---
title: "Włączanie i wyłączanie usług OLE DB | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OLE DB services [OLE DB], enabling and disabling
- service providers [OLE DB]
ms.assetid: 445f97eb-32a8-41c2-ad26-1169f78a074f
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 59b1a50c44d5719cf3c699a14e5139d9e9816938
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="enabling-and-disabling-ole-db-services"></a>Włączanie i wyłączanie usług OLE DB
Menedżer składników usługi OLE DB porównuje właściwości określony przez klienta do obsługiwanych przez dostawcę do określenia, czy usługi poszczególne składniki można wywoływane w celu zaspokojenia rozszerzonej funkcjonalności żądanej przez klienta. Na przykład jeśli aplikacja żąda przewijanego kursora, dostawca obsługuje tylko kursora tylko do przodu usługi Menedżer składników wywołuje składnik usługi Aparat kursora klienta umożliwiają korzystanie z funkcji przewijanego. Jeśli aplikacja jest zależne rozszerzone funkcje obsługiwane domyślnie na wierszy dostawcy i aplikacja nie jawnie ustawiona właściwości na żądanie, że funkcje, funkcje mogą nie być wyświetlane na zestaw wierszy zwrócony przez klienta Aparat kursora. Być interoperacyjne, aplikacje zawsze właściwości należy ustawić na jawne żądanie rozszerzonej funkcjonalności w razie potrzeby.  
  
 W niektórych przypadkach może być konieczne wyłączenie poszczególnych usług OLE DB do sprawnej współpracy z istniejących aplikacji, które zakładają właściwości dostawcy. Usługi OLE DB zapewniają możliwość wyłączenia poszczególnych usług lub wszystkich usług, na podstawie połączenia przez połączenie lub dla wszystkich aplikacji przy użyciu jednego dostawcy.  
  
## <a name="see-also"></a>Zobacz też  
 [Buforowanie zasobów i usługi OLE DB](../../data/oledb/ole-db-resource-pooling-and-services.md)