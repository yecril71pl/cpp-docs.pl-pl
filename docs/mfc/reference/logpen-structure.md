---
title: Struktura LOGPEN | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- LOGPEN
dev_langs:
- C++
helpviewer_keywords:
- LOGPEN structure [MFC]
ms.assetid: a89e8690-6b61-4af5-990c-7c82da24f3b0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c677f86a44d24e0d0d2742d47ee1534532001528
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2018
ms.locfileid: "37338535"
---
# <a name="logpen-structure"></a>Struktura LOGPEN
`LOGPEN` Struktury definiuje styl, szerokość i kolor pióra, rysunek używany do rysowania linii i obramowanie. [CPen::CreatePenIndirect](../../mfc/reference/cpen-class.md#createpenindirect) używa funkcji `LOGPEN` struktury.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef struct tagLOGPEN {  /* lgpn */  
    UINT lopnStyle;  
    POINT lopnWidth;  
    COLORREF lopnColor;  
} LOGPEN;  
```  
  
#### <a name="parameters"></a>Parametry  
 *lopnStyle*  
 Określa typ pióra. Ten element członkowski może być jednym z następujących wartości:  
  
- PS_SOLID tworzy pełny pióra.  
  
- PS_DASH tworzy kreskowane pióra. (Prawidłowe tylko wtedy, gdy szerokość pióra 1).  
  
- PS_DOT tworzy kropkowana pióra. (Prawidłowe tylko wtedy, gdy szerokość pióra 1).  
  
- Tworzy PS_DASHDOT pióra ze zmieniającymi się kreski oraz kropki. (Prawidłowe tylko wtedy, gdy szerokość pióra 1).  
  
- Tworzy PS_DASHDOTDOT a pióra ze zmieniającymi się łączniki i kropki double. (Prawidłowe tylko wtedy, gdy szerokość pióra 1).  
  
- PS_NULL tworzy pióra o wartości null.  
  
- PS_INSIDEFRAME tworzy produkowane przez Pióro, który rysuje wewnątrz ramki kształty zamknięte w GDI dane wyjściowe funkcji, które określają prostokąt otaczający (na przykład `Ellipse`, `Rectangle`, `RoundRect`, `Pie`, i `Chord` elementu członkowskiego funkcje). Gdy ten styl jest używany z użyciem interfejsu GDI dane wyjściowe funkcji, które nie określaj prostokąt otaczający (na przykład `LineTo` składowa), obszaru rysowania pióra nie jest ograniczone przez ramkę.  
  
     Jeśli styl PS_INSIDEFRAME i kolor, który nie pasuje do koloru w tabeli kolorów logiczne pióra, pióro jest rysowana szarych kolorem. Styl pióra PS_SOLID, nie może służyć do tworzenia pióra szarych kolorem. Styl PS_INSIDEFRAME jest taka sama jak PS_SOLID, jeśli szerokość pióra jest mniejsza niż lub równa 1.  
  
     Gdy styl PS_INSIDEFRAME jest używany z obiektami interfejsu GDI produkowane przez funkcje inne niż `Ellipse`, `Rectangle`, i `RoundRect`, wiersz nie może być całkowicie wewnątrz ramki o określonym.  
  
 *lopnWidth*  
 Określa szerokość pióra w jednostkach logicznych. Jeśli `lopnWidth` elementu członkowskiego wynosi 0, Pióro szerokości na urządzeniach rastrowych niezależnie od tego, w bieżącym trybie mapowanie 1 piksela.  
  
 *lopnColor*  
 Określa kolor pióra.  
  
## <a name="remarks"></a>Uwagi  
 `y` Wartość w [punktu](../../mfc/reference/point-structure1.md) struktury dla `lopnWidth` element nie jest używany.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** wingdi.h  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CPen::CreatePenIndirect](../../mfc/reference/cpen-class.md#createpenindirect)

