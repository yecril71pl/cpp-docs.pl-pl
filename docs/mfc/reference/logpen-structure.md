---
title: Struktura LOGPEN | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: LOGPEN
dev_langs: C++
helpviewer_keywords: LOGPEN structure [MFC]
ms.assetid: a89e8690-6b61-4af5-990c-7c82da24f3b0
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b7bfa598a59f62c11dbda13356559816b5bd47ad
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="logpen-structure"></a>Struktura LOGPEN
`LOGPEN` Definiuje struktury, style, szerokość i kolor pióra, rysunek używany do rysowania linii i obramowania. [CPen::CreatePenIndirect](../../mfc/reference/cpen-class.md#createpenindirect) używa `LOGPEN` struktury.  
  
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
 Określa typ pióra. Ten element członkowski może być jedną z następujących wartości:  
  
- **PS_SOLID** tworzy stałe pióra.  
  
- **PS_DASH** tworzy kreskowane pióra. (Prawidłowe tylko wtedy, gdy szerokość pióra 1).  
  
- **PS_DOT** tworzy kropkowanej pióra. (Prawidłowe tylko wtedy, gdy szerokość pióra 1).  
  
- **PS_DASHDOT** tworzy pióra ze zmieniającymi się łączniki i kropki. (Prawidłowe tylko wtedy, gdy szerokość pióra 1).  
  
- **PS_DASHDOTDOT** tworzy pióra ze zmieniającymi się łączniki i kropki dwa razy. (Prawidłowe tylko wtedy, gdy szerokość pióra 1).  
  
- **PS_NULL** tworzy pióra wartości null.  
  
- **PS_INSIDEFRAME** tworzy Pióro rysuje wewnątrz ramki kształty zamknięte utworzone za pomocą GDI dane wyjściowe funkcji określające prostokąt ograniczający (na przykład **elipsy**, **prostokąt**, `RoundRect`, `Pie`, i `Chord` funkcji elementów członkowskich). Gdy ten styl jest używany z GDI output funkcje, które nie określają prostokąt ograniczający (na przykład `LineTo` funkcji członkowskiej), obszaru rysowania pióra nie jest ograniczona przez ramki.  
  
     Jeśli ma pióra **PS_INSIDEFRAME** styl i kolor, który jest niezgodny z kolorów w tabeli kolorów logicznej pióra jest rysowany z kolor symulowany. **PS_SOLID** styl pióra nie może służyć do tworzenia pióra symulowanych kolorem. **PS_INSIDEFRAME** styl jest taki sam jak **PS_SOLID** Jeśli szerokość pióra jest mniejsza niż lub równa 1.  
  
     Gdy **PS_INSIDEFRAME** styl jest używany z innych niż utworzone za pomocą funkcji Obiekty GDI **elipsy**, **prostokąt**, i `RoundRect`, wiersz nie może być całkowicie w określonej ramce.  
  
 *lopnWidth*  
 Określa szerokość pióra w jednostkach logicznych. Jeśli **lopnWidth** elementu członkowskiego wynosi 0, Pióro na urządzeniach rastrowe niezależnie od bieżącego trybu mapowania szerokości 1 piksela.  
  
 *lopnColor*  
 Określa kolor pióra.  
  
## <a name="remarks"></a>Uwagi  
 **y** wartość w [punktu](../../mfc/reference/point-structure1.md) struktury **lopnWidth** element nie jest używany.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** wingdi.h  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CPen::CreatePenIndirect](../../mfc/reference/cpen-class.md#createpenindirect)

