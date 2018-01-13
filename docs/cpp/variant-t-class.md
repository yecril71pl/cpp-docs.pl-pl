---
title: "_variant_t — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: _variant_t
dev_langs: C++
helpviewer_keywords:
- _variant_t class [C++], operators
- _variant_t class
- _variant_t class [C++], member functions
- VARIANT object
- VARIANT object [C++], COM encapsulation
ms.assetid: 6a3cbd4e-0ae8-425e-b4cf-ca0df894c93f
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a670d18ab64637b54b063cfeb38f8d0cd8fee5d4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="variantt-class"></a>_variant_t — Klasa
**Dotyczące firmy Microsoft**  
  
 A `_variant_t` hermetyzuje `VARIANT` — typ danych. Klasa zarządza alokacji zasobów i dezalokacji i wykonywania wywołań funkcji do **VariantInit** i **VariantClear** odpowiednio.  
  
### <a name="construction"></a>Konstrukcji  
  
|||  
|-|-|  
|[_variant_t —](../cpp/variant-t-variant-t.md)|Konstruuje `_variant_t` obiektu.|  
  
### <a name="operations"></a>Operacje  
  
|||  
|-|-|  
|[Attach](../cpp/variant-t-attach.md)|Dołącza **VARIANT** obiekt do `_variant_t` obiektu.|  
|[Wyczyść](../cpp/variant-t-clear.md)|Czyści hermetyzowany **VARIANT** obiektu.|  
|[ChangeType](../cpp/variant-t-changetype.md)|Zmienia typ `_variant_t` wskazany obiekt **VARTYPE**.|  
|[Detach](../cpp/variant-t-detach.md)|Odłącza hermetyzowany **VARIANT** obiektu z tego `_variant_t` obiektu.|  
|[SetString](../cpp/variant-t-setstring.md)|Przypisuje to ciąg `_variant_t` obiektu.|  
  
### <a name="operators"></a>Operatory  
  
|||  
|-|-|  
|[Operator =](../cpp/variant-t-operator-equal.md)|Przypisuje nową wartość do istniejącej `_variant_t` obiektu.|  
|[operator ==,! =](../cpp/variant-t-relational-operators.md)|Porównać dwa `_variant_t` obiektów równości i nierówności.|  
|[Ekstraktory](../cpp/variant-t-extractors.md)|Wyodrębnianie danych z hermetyzowany **VARIANT** obiektu.|  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** comutil.h  
  
 **Lib:** comsuppw.lib lub comsuppwd.lib (zobacz [/Zc: wchar_t (wchar_t jest typem natywnym)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) Aby uzyskać więcej informacji)  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator klas obsługi COM](../cpp/compiler-com-support-classes.md)