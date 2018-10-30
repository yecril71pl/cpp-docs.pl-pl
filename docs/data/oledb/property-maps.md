---
title: Mapy właściwości | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/24/2018
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
ms.openlocfilehash: 2c6c3ddc4b19cd9b65203d8a5e675b9ed75720a1
ms.sourcegitcommit: 840033ddcfab51543072604ccd5656fc6d4a5d3a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2018
ms.locfileid: "50216464"
---
# <a name="property-maps"></a>Mapy właściwości

Polecenie opcjonalne obiektu sesji, wierszy i każdy dostawca obsługuje co najmniej jednej właściwości. Te właściwości są definiowane w mapy właściwości przechowywane w plikach nagłówkowych, utworzone przez **OLE DB Provider kreatora**. Każdy plik nagłówka zawiera mapę do właściwości w grupie właściwości OLE DB, które są zdefiniowane dla obiektu lub obiektów zdefiniowanych w tym pliku. Plik nagłówka, który zawiera obiekt źródła danych zawiera także map właściwości dla [właściwości DataSource](https://msdn.microsoft.com/library/ms724188). `Session.h` zawiera map właściwości dla [właściwości sesji](/previous-versions/windows/desktop/ms714221). Obiekt zestawu wierszy i polecenia są w pliku nagłówka jednego o nazwie *projectname*RS.h. Te właściwości są elementami członkowskimi [właściwości zestawu wierszy](/previous-versions/windows/desktop/ms711252) grupy.

## <a name="see-also"></a>Zobacz też

[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
