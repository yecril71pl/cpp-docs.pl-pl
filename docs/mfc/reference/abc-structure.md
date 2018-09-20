---
title: Struktura ABC | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- ABC
dev_langs:
- C++
helpviewer_keywords:
- ABC structure [MFC]
ms.assetid: 32663839-c3b7-4f47-896c-b15329c96bc8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6a977e3f0efd763ee416348f11e3c6b016c0d42e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46373715"
---
# <a name="abc-structure"></a>Struktura ABC

`ABC` Struktura zawiera szerokość znaku czcionki TrueType.

## <a name="syntax"></a>Składnia

```
typedef struct _ABC { /* abc */
    int abcA;
    UINT abcB;
    int abcC;
} ABC;
```

#### <a name="parameters"></a>Parametry

*abcA*<br/>
Określa odstępy A znaku. Element jest odległość do dodania do bieżącego położenia przed narysowaniem symbol znaku.

*abcB*<br/>
Określa odstępy B znaku. Odstępy B jest szerokość rysowane część symbol znaku.

*abcC*<br/>
Określa odstępy C znaku. Odstępy C jest odległość, aby dodać do aktualnej pozycji, aby zapewnić biały znak z prawej strony symbolu znaku.

## <a name="remarks"></a>Uwagi

Łączna szerokość znaku jest sumą A, B i C miejsca do magazynowania. Element lub miejsca C może być ujemna na wskazywać underhangs lub znacznego udziału.

## <a name="requirements"></a>Wymagania

**Nagłówek:** wingdi.h

## <a name="see-also"></a>Zobacz też

[Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDC::GetCharABCWidths](../../mfc/reference/cdc-class.md#getcharabcwidths)


