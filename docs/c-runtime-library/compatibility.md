---
title: Zgodność | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.programs
dev_langs:
- C++
helpviewer_keywords:
- CRT, compatibility
- compatibility, C run-time libraries
- compatibility
ms.assetid: 346709cb-edda-4909-9a19-3d253eddb6b7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d28f7ec22975464aca60ccdb743bbfd29c55cd81
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46094406"
---
# <a name="compatibility"></a>Zgodność

Uniwersalne biblioteki wykonawczej języka C (UCRT) obsługuje większość standardowej biblioteki C wymagane dla zgodności języka C++. Implementuje C99 (ISO/IEC 9899:1999) biblioteki, z wyjątkiem makra typu ogólnego, zdefiniowane w pliku \<tgmath.h >, a zgodność typów ścisłych w \<complex.h >. UCRT implementuje również dużego podzbioru POSIX.1 (ISO/IEC 9945-1:1996, interfejs aplikacji systemu POSIX) biblioteki C, ale nie jest w pełni zgodność na dowolnym określonym standard POSIX.  Ponadto UCRT implementuje kilka funkcji specyficznych dla firmy Microsoft i makra, które nie są częścią standardowej.

Funkcje specyficzne dla implementacji Microsoft Visual C++ znajdują się w bibliotece vcruntime.  Wiele z tych funkcji są przeznaczone do użytku wewnętrznego i nie może być wywoływany przez kod użytkownika. Niektóre opisano do użytku w zgodności debugowania i wdrażania.

C++ standard zastrzega sobie nazwy rozpoczynające się od znaku podkreślenia w globalnej przestrzeni nazw do implementacji. Ponieważ funkcje POSIX znajdują się w globalnej przestrzeni nazw, ale nie są częścią standardowej biblioteki C w czasie wykonywania, implementacje specyficzne dla firmy Microsoft z tych funkcji ma wiodącego podkreślenia. Do celów przenośności UCRT obsługuje również domyślne nazwy, ale kompilator języka Visual C++ generuje ostrzeżenie o zakończeniu obsługi, gdy kod, który używa tych jest kompilowany. Nazwy POSIX domyślne są przestarzałe, nie funkcji. Aby pominąć to ostrzeżenie, należy zdefiniować `_CRT_NONSTDC_NO_WARNINGS` przed dołączeniem żadnych nagłówków w kodzie, który używa oryginalnej nazwy POSIX.

Niektórych funkcji w standardowej biblioteki C ma historię użycia niebezpieczne, ze względu na parametry użyte i bufory niezaznaczone. Funkcje te są często źródła problemów z zabezpieczeniami w kodzie. Firma Microsoft utworzyła zbiór bezpieczniejsze wersje tych funkcji, które sprawdzają użycia parametrów i wywołać procedurę obsługi nieprawidłowego parametru, gdy problem zostanie wykryty w czasie wykonywania.  Domyślnie kompilator języka Visual C++ generuje wycofywania ostrzeżenia, gdy używana jest funkcja, zawierającej bezpieczniejsze wariant dostępne. Podczas kompilowania kodu jako języka C++, można zdefiniować `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` jako 1, aby wyeliminować ostrzeżenia większość. Ta metoda korzysta przeciążenia szablonu do wywoływania wariantów bezpieczniejsze przy zachowaniu kod przenośny źródła. Aby pominąć to ostrzeżenie, należy zdefiniować `_CRT_SECURE_NO_WARNINGS` przed dołączeniem żadnych nagłówków w kodzie, który korzysta z tych funkcji. Aby uzyskać więcej informacji, zobacz [funkcje zabezpieczeń w CRT](../c-runtime-library/security-features-in-the-crt.md).

Z wyjątkiem wymienionych w dokumentacji dla określonych funkcji UCRT jest zgodny z interfejsu API Windows.  Niektóre funkcje nie są obsługiwane w aplikacjach systemu Windows 8 Store lub w aplikacjach Windows platformy Uniwersalnej systemu Windows 10. Te funkcje są wymienione w [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md), która wylicza funkcje nie są obsługiwane przez środowisko wykonawcze Windows i [platformy uniwersalnej systemu Windows](/uwp).

## <a name="related-articles"></a>Powiązane artykuły

|Tytuł|Opis|
|-----------|-----------------|
|[Aplikacje platformy uniwersalnej systemu Windows, środowisko uruchomieniowe systemu Windows i środowisko wykonawcze języka C](../c-runtime-library/windows-store-apps-the-windows-runtime-and-the-c-run-time.md)|Opisuje, kiedy procedury UCRT nie są zgodne z aplikacji Universal Windows lub aplikacji Microsoft Store.|
|[Zgodność ANSI-C](../c-runtime-library/ansi-c-compliance.md)|W tym artykule opisano, zgodne standard nazewnictwa w UCRT.|
|[UNIX](../c-runtime-library/unix.md)|Zawiera wskazówki dotyczące przenoszenia programów do systemu UNIX.|
|[Platformy systemu Windows (CRT)](../c-runtime-library/windows-platforms-crt.md)|Wyświetla listę systemów operacyjnych, które są obsługuje CRT.|
|[Zgodność ze starszymi wersjami](../c-runtime-library/backward-compatibility.md)|W tym artykule opisano sposób mapowania starych nazw CRT na nowe licencje.|
|[Biblioteka CRT, funkcje](../c-runtime-library/crt-library-features.md)|Zawiera omówienie plików biblioteki (.lib) CRT i opcje kompilatora skojarzone.|