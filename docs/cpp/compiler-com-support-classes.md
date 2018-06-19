---
title: Kompilator klas obsługi COM | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_raise_error
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 6d800d9b-b902-4033-9639-740a30b06f88
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f4fe4e7c26d1b32f16d524407279e5e71534d00c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32411247"
---
# <a name="compiler-com-support-classes"></a>Kompilator klas obsługi COM
**Microsoft Specific**  
  
 Standardowa klas są używane do obsługi typów COM. Klasy są zdefiniowane w \<comdef.h > i pliki nagłówkowe wygenerowane z biblioteki typów.  
  
|Class|Cel|  
|-----------|-------------|  
|[_bstr_t](../cpp/bstr-t-class.md)|Opakowuje `BSTR` typu zapewnienie przydatne operatory i metody.|  
|[_com_error](../cpp/com-error-class.md)|Definiuje obiekt błąd zgłoszony przez [_com_raise_error —](../cpp/com-raise-error.md) w większość awarii.|  
|[_com_ptr_t](../cpp/com-ptr-t-class.md)|Hermetyzuje wskaźników interfejsów COM. i zautomatyzować wymagane wywołań `AddRef`, **wersji**, i `QueryInterface`.|  
|[_variant_t](../cpp/variant-t-class.md)|Opakowuje **VARIANT** typu zapewnienie przydatne operatory i metody.|  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa kompilatora COM](../cpp/compiler-com-support.md)   
 [Funkcje globalne kompilatora COM](../cpp/compiler-com-global-functions.md)   
 [Dokumentacja języka C++](../cpp/cpp-language-reference.md)