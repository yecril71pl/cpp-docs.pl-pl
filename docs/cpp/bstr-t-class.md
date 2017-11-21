---
title: "_bstr_t — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: _bstr_t
dev_langs: C++
helpviewer_keywords:
- BSTR object
- _bstr_t class
- BSTR object [C++], COM encapsulation
ms.assetid: 58841fef-fe21-4a84-aab9-780262b5201f
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0af38fe5e88540bf7e8947808c49c5283d742a4a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="bstrt-class"></a>_bstr_t — Klasa
**Dotyczące firmy Microsoft**  
  
 A `_bstr_t` hermetyzuje [BSTR, typ danych](http://msdn.microsoft.com/en-us/1b2d7d2c-47af-4389-a6b6-b01b7e915228). Klasa zarządza alokacji zasobów i dezalokacji za pośrednictwem wywołania funkcji **SysAllocString** i **SysFreeString** i innych `BSTR` interfejsów API, gdy jest to konieczne. `_bstr_t` Klasy używa zliczanie, aby uniknąć nadmiernego obciążenia.  
  
### <a name="construction"></a>Konstrukcji  
  
|||  
|-|-|  
|[_bstr_t —](../cpp/bstr-t-bstr-t.md)|Konstruuje `_bstr_t` obiektu.|  
  
### <a name="operations"></a>Operacje  
  
|||  
|-|-|  
|[Przypisz](../cpp/bstr-t-assign.md)|Kopie `BSTR` do `BSTR` opakowane przez `_bstr_t`.|  
|[Dołącz](../cpp/bstr-t-attach.md)|Łącza `_bstr_t` otoki do `BSTR`.|  
|[Kopiuj](../cpp/bstr-t-copy.md)|Tworzy kopię hermetyzowany `BSTR`.|  
|[Odłączanie](../cpp/bstr-t-detach.md)|Zwraca `BSTR` opakowane przez `_bstr_t` i odłącza `BSTR` z `_bstr_t`.|  
|[GetAddress](../cpp/bstr-t-getaddress.md)|Wskazuje `BSTR` opakowane przez `_bstr_t`.|  
|[GetBSTR](../cpp/bstr-t-getbstr.md)|Wskazuje początek `BSTR` opakowane przez `_bstr_t`.|  
|[długość](../cpp/bstr-t-length.md)|Zwraca liczbę znaków w `_bstr_t`.|  
  
### <a name="operators"></a>Operatory  
  
|||  
|-|-|  
|[operator =](../cpp/bstr-t-operator-equal.md)|Przypisuje nową wartość do istniejącej `_bstr_t` obiektu.|  
|[+= — operator](../cpp/bstr-t-operator-add-equal-plus.md)|Dołącza znaki na końcu `_bstr_t` obiektu.|  
|[operator +](../cpp/bstr-t-operator-add-equal-plus.md)|Łączy dwa ciągi.|  
|[operator!](../cpp/bstr-t-operator-logical-not.md)|Sprawdza, czy hermetyzowany `BSTR` jest **NULL** ciągu.|  
|[operator ==,! =, \<, >, \<=, > =](../cpp/bstr-t-relational-operators.md)|Porównuje dwa `_bstr_t` obiektów.|  
|[Operator wchar_t * &#124; char\*](../cpp/bstr-t-wchar-t-star-bstr-t-char-star.md)|Wyodrębnij wskaźniki do hermetyzowany Unicode lub wielobajtowe `BSTR` obiektu.|  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** comutil.h  
  
 **Lib:** comsuppw.lib lub comsuppwd.lib (zobacz [/Zc: wchar_t (wchar_t jest typem natywnym)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) Aby uzyskać więcej informacji)  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator klas obsługi COM](../cpp/compiler-com-support-classes.md)