---
title: _bstr_t — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _bstr_t
dev_langs:
- C++
helpviewer_keywords:
- BSTR object
- _bstr_t class
- BSTR object [C++], COM encapsulation
ms.assetid: 58841fef-fe21-4a84-aab9-780262b5201f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f7cb3d05997cfe3d803f522962ed9e7382269bd3
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2018
ms.locfileid: "39404928"
---
# <a name="bstrt-class"></a>_bstr_t — Klasa
**Microsoft Specific**  
  
 A `_bstr_t` hermetyzuje [typ danych](http://msdn.microsoft.com/1b2d7d2c-47af-4389-a6b6-b01b7e915228). Klasa zarządza alokacją i dezalokacją za pośrednictwem wywołania funkcji zasobów `SysAllocString` i `SysFreeString` i innych `BSTR` interfejsów API, gdy jest to konieczne. **_Bstr_t** klasa używa zliczania odniesień, by uniknąć nadmiernego obciążenia.  
  
### <a name="construction"></a>Konstrukcja  
  
|||  
|-|-|  
|[_bstr_t](../cpp/bstr-t-bstr-t.md)|Konstruuje `_bstr_t` obiektu.|  
  
### <a name="operations"></a>Operacje  
  
|||  
|-|-|  
|[Przypisz](../cpp/bstr-t-assign.md)|Kopiuje `BSTR` do `BSTR` opakowane przez `_bstr_t`.|  
|[Attach](../cpp/bstr-t-attach.md)|Linki `_bstr_t` opakowanie `BSTR`.|  
|[Kopiuj](../cpp/bstr-t-copy.md)|Tworzy kopię zhermetyzowanego `BSTR`.|  
|[Detach](../cpp/bstr-t-detach.md)|Zwraca `BSTR` opakowane przez `_bstr_t` oraz odłącza `BSTR` z `_bstr_t`.|  
|[Getaddress —](../cpp/bstr-t-getaddress.md)|Wskazuje `BSTR` opakowane przez `_bstr_t`.|  
|[GetBSTR](../cpp/bstr-t-getbstr.md)|Wskazuje początek `BSTR` opakowane przez `_bstr_t`.|  
|[Długość](../cpp/bstr-t-length.md)|Zwraca liczbę znaków w `_bstr_t`.|  
  
### <a name="operators"></a>Operatory  
  
|||  
|-|-|  
|[operator =](../cpp/bstr-t-operator-equal.md)|Przypisuje nową wartość do istniejącej `_bstr_t` obiektu.|  
|[+= — operator](../cpp/bstr-t-operator-add-equal-plus.md)|Dołącza znaki do końca `_bstr_t` obiektu.|  
|[operator +](../cpp/bstr-t-operator-add-equal-plus.md)|Łączy dwa ciągi.|  
|[operator !](../cpp/bstr-t-operator-logical-not.md)|Sprawdza, czy zhermetyzowany `BSTR` jest ciągiem o wartości NULL.|  
|[operator ==,! =, \<, >, \<=, > =](../cpp/bstr-t-relational-operators.md)|Porównuje dwa `_bstr_t` obiektów.|  
|[Operator wchar_t * &#124; char\*](../cpp/bstr-t-wchar-t-star-bstr-t-char-star.md)|Wyodrębnij wskaźniki do zhermetyzowanego Unicode lub wielobajtowego `BSTR` obiektu.|  
  
**END specyficzny dla Microsoft**  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<comutil.h >  
  
 **Lib:** comsuppw.lib lub comsuppwd.lib (zobacz [/Zc: wchar_t (wchar_t jest typem natywnym)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) Aby uzyskać więcej informacji)  
  
## <a name="see-also"></a>Zobacz także  
 [Kompilator klas obsługi COM](../cpp/compiler-com-support-classes.md)