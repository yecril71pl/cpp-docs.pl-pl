---
title: Mapy właściwości
ms.date: 10/24/2018
helpviewer_keywords:
- OLE DB providers, properties
- maps, property
- property maps
ms.assetid: 44abde56-90ad-4612-854e-d2fa5426fa80
ms.openlocfilehash: 2d01c2f0d7fb581f9f7e93c1ec100e465a6d92f3
ms.sourcegitcommit: c40469825b6101baac87d43e5f4aed6df6b078f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2018
ms.locfileid: "51556486"
---
# <a name="property-maps"></a>Mapy właściwości

Polecenie opcjonalne obiektu sesji, wierszy i każdy dostawca obsługuje co najmniej jednej właściwości. Te właściwości są definiowane w mapy właściwości przechowywane w plikach nagłówkowych, utworzone przez **OLE DB Provider kreatora**. Każdy plik nagłówka zawiera mapę do właściwości w grupie właściwości OLE DB, które są zdefiniowane dla obiektu lub obiektów zdefiniowanych w tym pliku. Plik nagłówka, który zawiera obiekt źródła danych zawiera także map właściwości dla [właściwości DataSource](https://msdn.microsoft.com/library/ms724188). `Session.h` zawiera map właściwości dla [właściwości sesji](https://docs.microsoft.com/previous-versions/windows/desktop/ms714221(v=vs.85)). Obiekt zestawu wierszy i polecenia są w pliku nagłówka jednego o nazwie *projectname*RS.h. Te właściwości są elementami członkowskimi [właściwości zestawu wierszy](https://docs.microsoft.com/previous-versions/windows/desktop/ms711252(v=vs.85)) grupy.

## <a name="see-also"></a>Zobacz też

[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
