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
ms.openlocfilehash: 7dc931e643235bc6edb4a1121628ac5185b76cc7
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2018
ms.locfileid: "39402552"
---
# <a name="compiler-com-support-classes"></a>Kompilator klas obsługi COM
**Microsoft Specific**  
  
 Standardowych klas są używane do obsługi niektórych typów modelu COM. Klasy są zdefiniowane w \<comdef.h > i pliki nagłówkowe wygenerowane z biblioteki typów.  
  
|Class|Cel|  
|-----------|-------------|  
|[_bstr_t](../cpp/bstr-t-class.md)|Opakowuje `BSTR` typu przydatne operatory i metody.|  
|[_com_error](../cpp/com-error-class.md)|Definiuje obiekt błędu zgłoszony przez [_com_raise_error —](../cpp/com-raise-error.md) w większości błędów.|  
|[_com_ptr_t](../cpp/com-ptr-t-class.md)|Hermetyzuje wskaźniki interfejsu COM i automatyzuje wymaganego wywołania `AddRef`, `Release`, i `QueryInterface`.|  
|[_variant_t](../cpp/variant-t-class.md)|Opakowuje `VARIANT` typu przydatne operatory i metody.|  
  
**END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz także  
 [Obsługa kompilatora COM](../cpp/compiler-com-support.md)   
 [Funkcje globalne kompilatora COM](../cpp/compiler-com-global-functions.md)   
 [Dokumentacja języka C++](../cpp/cpp-language-reference.md)