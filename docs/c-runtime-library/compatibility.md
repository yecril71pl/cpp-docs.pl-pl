---
title: "Zgodność | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: c.programs
dev_langs: C++
helpviewer_keywords:
- CRT, compatibility
- compatibility, C run-time libraries
- compatibility
ms.assetid: 346709cb-edda-4909-9a19-3d253eddb6b7
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f14d330ada8f71cc3556b7151189968b43cff4ca
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compatibility"></a>Zgodność
Uniwersalny biblioteki Biblioteka (C Run-Time UCRT) obsługuje większość biblioteki standardowe C wymaganej do zgodność języka C++. Implementuje C99 biblioteki (ISO/IEC 9899:1999), z wyjątkiem makra ogólny typ zdefiniowany w \<tgmath.h >, a ścisłe zasady zgodności w \<complex.h >. Biblioteka UCRT też implementuje podzbiór dużych POSIX.1 (ISO/IEC 9945-1:1996, interfejs aplikacji systemu POSIX) biblioteki C, ale nie jest w pełni zgodność na dowolnym określonym standard POSIX.  Ponadto biblioteka UCRT implementuje kilka funkcje specyficzne dla firmy Microsoft i makra, które nie są częścią standardowej.  
  
 Funkcje specyficzne dla wdrożenia programu Microsoft Visual c++ znajdują się w bibliotece vcruntime.  Wiele z tych funkcji służą do użytku wewnętrznego i nie może być wywoływany przez kod użytkownika. Niektóre opisano do użycia w zgodności debugowania i implementacji.  
  
 C++ standard rezerwuje nazwy zaczynające się od znaku podkreślenia w globalnej przestrzeni nazw do implementacji. Ponieważ funkcje POSIX znajdują się w globalnej przestrzeni nazw, ale nie są częścią standardowej biblioteki wykonawczej C, implementacje specyficzne dla firmy Microsoft z tych funkcji ma wiodącego podkreślenia. Przenośności Biblioteka UCRT obsługuje również domyślne nazwy, ale kompilatora Visual C++ generuje ostrzeżenie podczas kompilowania kodu, który używa tych. Nazwy POSIX domyślne są traktowane jako przestarzałe, nie funkcji. Aby pominąć to ostrzeżenie, zdefiniuj `_CRT_NONSTDC_NO_WARNINGS` przed dołączeniem żadnych nagłówków w kodzie, który używa oryginalnych nazw POSIX.  
  
 Niektóre funkcje standardowej biblioteki C ma historię użycia niebezpieczny, ze względu na parametry użyte i buforów niezaznaczone. Funkcje te są często źródło problemów z zabezpieczeniami w kodzie. Firma Microsoft opracowała zestaw bezpieczniejsze wersje tych funkcji, które sprawdzają użycia parametrów i wywołania program obsługi nieprawidłowych parametrów, gdy zostanie wykryty problem w czasie wykonywania.  Domyślnie kompilatora Visual C++ wystawia amortyzacja ostrzeżenie, gdy używana jest funkcja ma dostępne wariant bezpieczniejsze. Podczas kompilowania kodu jako C++ można zdefiniować `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` jako 1, aby wyeliminować większość ostrzeżenia. Wywołaj bezpieczniejsze wariantów przy zachowaniu kodu źródłowego przenośne używa przeciążenia szablonu. Aby pominąć to ostrzeżenie, zdefiniuj `_CRT_SECURE_NO_WARNINGS` przed dołączeniem żadnych nagłówków w kodzie, który używa tych funkcji. Aby uzyskać więcej informacji, zobacz [funkcje zabezpieczeń w CRT](../c-runtime-library/security-features-in-the-crt.md).  
  
 Z wyjątkiem przypadków wymienionych w dokumentacji dla określonych funkcji, biblioteka UCRT jest zgodny z interfejsu API systemu Windows.  Niektóre funkcje nie są obsługiwane w aplikacjach Sklepu Windows 8 lub w aplikacji uniwersalnych systemu Windows w systemie Windows 10. Te funkcje są wymienione w [funkcje CRT, nie są obsługiwane z parametrem /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx), który wylicza funkcje nieobsługiwane przez [środowiska wykonawczego systemu Windows](http://msdn.microsoft.com/en-us/9a1a18b8-9802-4ec5-b9de-0d2dfdf414e9).  
  
## <a name="related-articles"></a>Powiązane artykuły  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Aplikacje sklepu Windows Store, środowisko uruchomieniowe systemu Windows i środowisko wykonawcze języka C](../c-runtime-library/windows-store-apps-the-windows-runtime-and-the-c-run-time.md)|Opisuje, gdy biblioteka UCRT procedury nie są zgodne z uniwersalnych aplikacji systemu Windows lub Sklepu Windows.|  
|[Zgodność ANSI-C](../c-runtime-library/ansi-c-compliance.md)|Opisuje zgodne standard nazewnictwa w Biblioteka UCRT.|  
|[UNIX](../c-runtime-library/unix.md)|Zawiera wskazówki dotyczące przenoszenia programów dla systemu UNIX.|  
|[Platformy systemu Windows (CRT)](../c-runtime-library/windows-platforms-crt.md)|Zawiera listę systemów operacyjnych, które są obsługuje CRT.|  
|[Zgodność ze starszymi wersjami](../c-runtime-library/backward-compatibility.md)|Opisuje sposób mapowania nazw CRT starego na nowe pliki.|  
|[Biblioteka CRT, funkcje](../c-runtime-library/crt-library-features.md)|Zawiera omówienie CRT plików bibliotek (lib) i opcje kompilatora skojarzone.|