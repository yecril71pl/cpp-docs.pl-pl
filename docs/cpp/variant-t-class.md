---
title: _variant_t — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _variant_t
dev_langs:
- C++
helpviewer_keywords:
- _variant_t class [C++], operators
- _variant_t class
- _variant_t class [C++], member functions
- VARIANT object
- VARIANT object [C++], COM encapsulation
ms.assetid: 6a3cbd4e-0ae8-425e-b4cf-ca0df894c93f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 70a3406d53296c778eba2ce9a6794afac2c846bd
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37939809"
---
# <a name="variantt-class"></a>_variant_t — Klasa
**Microsoft Specific**  
  
 A `_variant_t` hermetyzuje `VARIANT` typu danych. Klasa zarządza alokacją i dezalokacją zasobów i sprawia, że wywołania funkcji `VariantInit` i `VariantClear` odpowiednio.  
  
### <a name="construction"></a>Konstrukcja  
  
|||  
|-|-|  
|[_variant_t](../cpp/variant-t-variant-t.md)|Konstruuje `_variant_t` obiektu.|  
  
### <a name="operations"></a>Operacje  
  
|||  
|-|-|  
|[Attach](../cpp/variant-t-attach.md)|Dołącza `VARIANT` do obiektu `_variant_t` obiektu.|  
|[Usuń zaznaczenie](../cpp/variant-t-clear.md)|Czyści zhermetyzowany `VARIANT` obiektu.|  
|[ChangeType](../cpp/variant-t-changetype.md)|Zmienia typ `_variant_t` wskazany obiekt `VARTYPE`.|  
|[Detach](../cpp/variant-t-detach.md)|Odłącza zhermetyzowany `VARIANT` obiektu z tego `_variant_t` obiektu.|  
|[Setstring —](../cpp/variant-t-setstring.md)|Przypisuje ten ciąg `_variant_t` obiektu.|  
  
### <a name="operators"></a>Operatory  
  
|||  
|-|-|  
|[operator =](../cpp/variant-t-operator-equal.md)|Przypisuje nową wartość do istniejącej `_variant_t` obiektu.|  
|[operator ==,! =](../cpp/variant-t-relational-operators.md)|Porównanie dwóch `_variant_t` obiektów dla równości i nierówności.|  
|[Ekstraktory](../cpp/variant-t-extractors.md)|Wyodrębnianie danych z zhermetyzowany `VARIANT` obiektu.|  
  
**END specyficzny dla Microsoft**  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<comutil.h >  
  
 **Lib:** comsuppw.lib lub comsuppwd.lib (zobacz [/Zc: wchar_t (wchar_t jest typem natywnym)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) Aby uzyskać więcej informacji)  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator klas obsługi COM](../cpp/compiler-com-support-classes.md)