---
title: Zgodność
description: Opisuje zgodność biblioteki uniwersalnego środowiska uruchomieniowego języka Microsoft (UCRT) w standardowym języku C, POSIX, bezpieczny CRT i aplikacje ze sklepu.
ms.date: 12/06/2019
helpviewer_keywords:
- CRT, compatibility
- compatibility, C run-time libraries
- compatibility
ms.assetid: 346709cb-edda-4909-9a19-3d253eddb6b7
ms.openlocfilehash: 39b936acc43243973c2f66ef6fc7306026cc3259
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171050"
---
# <a name="compatibility"></a>Zgodność

Uniwersalna biblioteka uruchomieniowa C (UCRT) obsługuje większość standardowej biblioteki języka C, która jest wymagana C++ do zgodności. Implementuje bibliotekę C99 (ISO/IEC 9899:1999) z pewnymi wyjątkami: makra ogólne typu zdefiniowane w \<tgmath. h > i zgodność typu ścisłego w \<złożonym. h >. UCRT implementuje również duży Podzestaw systemu POSIX. 1 (ISO/IEC 9945-1:1996, systemowy interfejs programu aplikacji systemu POSIX) Biblioteka C. Nie jest to jednak w pełni zgodne z żadnym konkretnym standardem POSIX. UCRT implementuje także kilka funkcji i makr specyficznych dla firmy Microsoft, które nie są częścią standardu.

Funkcje specyficzne dla implementacji wizualizacji C++ firmy Microsoft są dostępne w bibliotece vcruntime.  Wiele z tych funkcji służy do użytku wewnętrznego i nie może zostać wywołane przez kod użytkownika. Niektóre z nich są udokumentowane pod kątem zgodności z debugowaniem i implementacją.

C++ Standardowe nazwy rezerw, które zaczynają się od znaku podkreślenia w globalnej przestrzeni nazw, do implementacji. Zarówno funkcje POSIX, jak i biblioteki środowiska uruchomieniowego specyficzne dla firmy Microsoft znajdują się w globalnej przestrzeni nazw, ale nie są częścią standardowej biblioteki środowiska uruchomieniowego C. Dlatego preferowane implementacje firmy Microsoft tych funkcji mają wiodący znak podkreślenia. W przypadku przenośności UCRT obsługuje również nazwy domyślne, ale kompilator firmy Microsoft C++ wystawia ostrzeżenie o zaniechaniu, gdy kod, który używa tych danych jest kompilowany. Tylko nazwy domyślne są przestarzałe, a nie same funkcje. Aby pominąć ostrzeżenie, zdefiniuj `_CRT_NONSTDC_NO_WARNINGS` przed dołączeniem nagłówków w kodzie, które używają oryginalnych nazw POSIX.

Niektóre funkcje w standardowej bibliotece C mają historię niebezpiecznego użycia z powodu nieużywanych parametrów i niesprawdzonych buforów. Te funkcje są często źródłem problemów z zabezpieczeniami w kodzie. Firma Microsoft stworzyła zestaw bezpieczniejszych wersji tych funkcji, które weryfikują użycie parametrów. Wywołują procedurę obsługi nieprawidłowego parametru w przypadku wykrycia problemu w czasie wykonywania.  Domyślnie kompilator firmy Microsoft C++ wystawia ostrzeżenie o zaniechaniu, gdy jest używana funkcja, która ma dostęp do bezpieczniejszej wariantu. Podczas kompilowania kodu jako C++można zdefiniować `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` jako 1 w celu wyeliminowania większości ostrzeżeń. To makro umożliwia przeciążenia szablonów wywoływanie bezpieczniejszych wariantów przy zachowaniu przenośnego kodu źródłowego. Aby pominąć ostrzeżenie, zdefiniuj `_CRT_SECURE_NO_WARNINGS` przed dołączeniem nagłówków w kodzie, które korzystają z tych funkcji. Aby uzyskać więcej informacji, zobacz [funkcje zabezpieczeń w CRT](../c-runtime-library/security-features-in-the-crt.md).

Z wyjątkiem sytuacji, w której zaznaczono w dokumentacji dotyczącej określonych funkcji, UCRT jest zgodny z interfejsem API systemu Windows.  Niektóre funkcje nie są obsługiwane w aplikacjach Windows Store i platforma uniwersalna systemu Windows ([platformy UWP](/uwp)). Te funkcje są wymienione w [funkcjach CRT nieobsługiwanych w aplikacjach platforma uniwersalna systemu Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="related-articles"></a>Powiązane artykuły

|Tytuł|Opis|
|-----------|-----------------|
|[Aplikacje platformy uniwersalnej systemu Windows, środowisko uruchomieniowe systemu Windows i środowisko wykonawcze języka C](../c-runtime-library/windows-store-apps-the-windows-runtime-and-the-c-run-time.md)|Opisuje, kiedy procedury UCRT są niezgodne z aplikacjami uniwersalnymi systemu Windows lub aplikacjami Microsoft Store.|
|[Zgodność ANSI-C](../c-runtime-library/ansi-c-compliance.md)|Opisuje zgodne ze standardami nazewnictwo w UCRT.|
|[UNIX](../c-runtime-library/unix.md)|Zawiera wytyczne dotyczące przenoszenia programów do systemu UNIX.|
|[Platformy systemu Windows (CRT)](../c-runtime-library/windows-platforms-crt.md)|Zawiera listę systemów operacyjnych obsługiwanych przez technologię CRT.|
|[Zgodność ze starszymi wersjami](../c-runtime-library/backward-compatibility.md)|Opisuje sposób mapowania starych nazw CRT na nowe.|
|[Biblioteka CRT, funkcje](../c-runtime-library/crt-library-features.md)|Zawiera omówienie plików biblioteki CRT (. lib) i skojarzonych z nimi opcji kompilatora.|
