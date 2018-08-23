---
title: Mapy właściwości | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, properties
- maps, property
- property maps
ms.assetid: 44abde56-90ad-4612-854e-d2fa5426fa80
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3cf0ad638e36fcfd99ff02281ee361cd702dbd27
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/14/2018
ms.locfileid: "42465897"
---
# <a name="property-maps"></a>Mapy właściwości
Oprócz obiektu polecenie opcjonalne sesję, wierszy i każdy dostawca obsługuje co najmniej jednej właściwości. Te właściwości są definiowane w mapy właściwości zawarte w plikach nagłówkowych, utworzone przez OLE DB Provider kreatora. Każdy plik nagłówka zawiera mapę do właściwości w grupie właściwości OLE DB, które są zdefiniowane dla obiektu lub obiektów zdefiniowanych w tym pliku. Plik nagłówka, który zawiera obiekt źródła danych zawiera także map właściwości dla [właściwości DataSource](https://msdn.microsoft.com/library/ms724188\(v=vs.140\).aspx). Session.h zawiera map właściwości dla [właściwości sesji](/previous-versions/windows/desktop/ms714221\(v=vs.85\)). Obiekty wierszy i polecenia znajdują się w pliku nagłówka jednego o nazwie *projectname*RS.h. Te właściwości są elementami członkowskimi [właściwości zestawu wierszy](/previous-versions/windows/desktop/ms711252\(v=vs.85\)) grupy.  
  
## <a name="see-also"></a>Zobacz też  
 [Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)