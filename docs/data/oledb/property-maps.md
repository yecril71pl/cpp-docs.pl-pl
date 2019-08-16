---
title: Mapy właściwości
ms.date: 10/24/2018
helpviewer_keywords:
- OLE DB providers, properties
- maps, property
- property maps
ms.assetid: 44abde56-90ad-4612-854e-d2fa5426fa80
ms.openlocfilehash: 79a65290c24ab016d9f81b54b9b7720d5c4ff352
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501289"
---
# <a name="property-maps"></a>Mapy właściwości

Przy użyciu sesji, zestawu wierszy i opcjonalnego obiektu polecenia każdy dostawca obsługuje jedną lub więcej właściwości. Te właściwości są zdefiniowane w mapach właściwości przechowywanych w plikach nagłówkowych utworzonych przez **Kreatora dostawcy OLE DB**. Każdy plik nagłówkowy zawiera mapę właściwości w OLE DB grupy właściwości zdefiniowane dla obiektu lub obiektów zdefiniowanych w tym pliku. Plik nagłówkowy, który zawiera obiekt źródła danych, zawiera również mapę właściwości [Właściwości DataSource](/previous-versions/windows/desktop/ms724188(v=vs.85)). `Session.h`zawiera mapę właściwości dla [właściwości sesji](/previous-versions/windows/desktop/ms714221(v=vs.85)). Zestaw wierszy i obiekty poleceń znajdują się w jednym pliku nagłówkowym o nazwie *ProjectName*RS. h. Te właściwości są elementami członkowskimi grupy [Właściwości zestawu wierszy](/previous-versions/windows/desktop/ms711252(v=vs.85)) .

## <a name="see-also"></a>Zobacz także

[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
