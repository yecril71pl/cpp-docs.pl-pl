---
title: Obsługa kompilatora COM | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 76a78442-f2a4-4985-9967-67e20773f847
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8d6e916cbd7cd8f5fbb259ff096159f9a49202ac
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="compiler-com-support"></a>Obsługa kompilatora COM
## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft  
 Kompilator Visual C++ bezpośrednio może odczytywać bibliotek typów model (COM) obiektu składnika i tłumaczenie zawartość do kodu źródłowego języka C++, która może być uwzględniony w kompilacji. Rozszerzenia językowe są dostępne dla ułatwienia COM programowania po stronie klienta.  
  
 Za pomocą [dyrektywy preprocesora #import](../preprocessor/hash-import-directive-cpp.md), kompilator może odczytać biblioteki typów i przekonwertować go do pliku nagłówka C++, który opisuje COM interfejsy klas. Zestaw `#import` atrybutów jest dostępna dla formantu użytkownika zawartości pliki wynikowe nagłówka biblioteki typów.  
  
 Można użyć [__declspec](../cpp/declspec.md) rozszerzonych atrybutów [uuid](../cpp/uuid-cpp.md) można przypisać do obiektu COM Unikatowy identyfikator globalny (GUID). Słowo kluczowe [__uuidof](../cpp/uuidof-operator.md) służy do wyodrębniania identyfikatora GUID skojarzony z obiektem COM. Inny `__declspec` atrybutu, [właściwości](../cpp/property-cpp.md), może służyć do określenia **uzyskać** i **ustawić** metody dla elementu członkowskiego danych obiektu COM.  
  
 Zestaw klasy i funkcje globalne obsługi modelu COM został dostarczony do obsługi **VARIANT** i `BSTR` typy, wdrożenie wskaźniki inteligentne i Hermetyzowanie obiektu błąd zgłoszony przez `_com_raise_error`:  
  
-   [Funkcje globalne kompilatora COM](../cpp/compiler-com-global-functions.md)  
  
-   [_bstr_t](../cpp/bstr-t-class.md)  
  
-   [_com_error](../cpp/com-error-class.md)  
  
-   [_com_ptr_t](../cpp/com-ptr-t-class.md)  
  
-   [_variant_t](../cpp/variant-t-class.md)  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator klas obsługi COM](../cpp/compiler-com-support-classes.md)   
 [Funkcje globalne kompilatora COM](../cpp/compiler-com-global-functions.md)