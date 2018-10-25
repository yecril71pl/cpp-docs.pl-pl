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
ms.openlocfilehash: bbed70f7871cb215a944a5143793b26b4196d7bc
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50052758"
---
# <a name="property-maps"></a>Mapy właściwości

Oprócz obiektu polecenie opcjonalne sesję, wierszy i każdy dostawca obsługuje co najmniej jednej właściwości. Te właściwości są definiowane w mapy właściwości zawarte w plikach nagłówkowych, utworzone przez OLE DB Provider kreatora. Każdy plik nagłówka zawiera mapę do właściwości w grupie właściwości OLE DB, które są zdefiniowane dla obiektu lub obiektów zdefiniowanych w tym pliku. Plik nagłówka, który zawiera obiekt źródła danych zawiera także map właściwości dla [właściwości DataSource](https://msdn.microsoft.com/library/ms724188). Session.h zawiera map właściwości dla [właściwości sesji](/previous-versions/windows/desktop/ms714221). Obiekty wierszy i polecenia znajdują się w pliku nagłówka jednego o nazwie *projectname*RS.h. Te właściwości są elementami członkowskimi [właściwości zestawu wierszy](/previous-versions/windows/desktop/ms711252) grupy.

## <a name="see-also"></a>Zobacz też

[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)