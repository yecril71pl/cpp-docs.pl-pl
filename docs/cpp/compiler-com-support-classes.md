---
title: "Kompilator klas obsługi COM | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: _com_raise_error
dev_langs: C++
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 6d800d9b-b902-4033-9639-740a30b06f88
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0e2ec9f0814c976a5ea175e0cd62ab8e57b02f1c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-com-support-classes"></a>Kompilator klas obsługi COM
**Dotyczące firmy Microsoft**  
  
 Standardowa klas są używane do obsługi typów COM. Klasy są zdefiniowane w comdef.h i pliki nagłówkowe wygenerowane z biblioteki typów.  
  
|Class|Cel|  
|-----------|-------------|  
|[_bstr_t —](../cpp/bstr-t-class.md)|Opakowuje `BSTR` typu zapewnienie przydatne operatory i metody.|  
|[_com_error](../cpp/com-error-class.md)|Definiuje obiekt błąd zgłoszony przez [_com_raise_error —](../cpp/com-raise-error.md) w większość awarii.|  
|[_com_ptr_t —](../cpp/com-ptr-t-class.md)|Hermetyzuje wskaźników interfejsów COM. i zautomatyzować wymagane wywołań `AddRef`, **wersji**, i `QueryInterface`.|  
|[_variant_t —](../cpp/variant-t-class.md)|Opakowuje **VARIANT** typu zapewnienie przydatne operatory i metody.|  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa kompilatora COM](../cpp/compiler-com-support.md)   
 [Funkcje globalne kompilatora COM](../cpp/compiler-com-global-functions.md)   
 [Dokumentacja języka C++](../cpp/cpp-language-reference.md)