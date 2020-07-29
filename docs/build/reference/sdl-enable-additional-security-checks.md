---
title: /sdl (Włącz dodatkowe kontrole zabezpieczeń)
ms.date: 11/26/2018
f1_keywords:
- VC.Project.VCCLCompilerTool.SDLCheck
ms.assetid: 3dcf86a0-3169-4240-9f29-e04a9f535826
ms.openlocfilehash: d5a85f9648ebcc4064146f22cf5da020e06b7ba3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218978"
---
# <a name="sdl-enable-additional-security-checks"></a>/sdl (Włącz dodatkowe kontrole zabezpieczeń)

Dodaje zalecane testy cyklu projektowania zabezpieczeń (SDL). Te testy obejmują dodatkowe ostrzeżenia związane z zabezpieczeniami jako błędy i dodatkowe funkcje bezpiecznego generowania kodu.

## <a name="syntax"></a>Składnia

> **`/sdl`**[**`-`**]

## <a name="remarks"></a>Uwagi

**/SDL** włącza nadzbiór kontroli zabezpieczeń linii bazowej dostarczonych przez [`/GS`](gs-buffer-security-check.md) i zastąpień **`/GS-`** . Domyślnie program **`/sdl`** jest wyłączony. **`/sdl-`** wyłącza dodatkowe sprawdzanie zabezpieczeń.

## <a name="compile-time-checks"></a>Sprawdzanie czasu kompilacji

**`/sdl`** włącza te ostrzeżenia jako błędy:

|Ostrzeżenie włączone przez/SDL|Równoważny przełącznik wiersza polecenia|Opis|
|------------------------------|-------------------------------------|-----------------|
|[C4146](../../error-messages/compiler-warnings/compiler-warning-level-2-c4146.md)|/we4146|Jednoargumentowy operator minus został zastosowany do typu bez znaku, co spowoduje powstanie niepodpisanego wyniku.|
|[C4308](../../error-messages/compiler-warnings/compiler-warning-level-2-c4308.md)|/we4308|Ujemna stała całkowita przekonwertowana na typ bez znaku, co może oznaczać, że jest to niemożliwy wynik.|
|[C4532](../../error-messages/compiler-warnings/compiler-warning-level-1-c4532.md)|/we4532|Użycie `continue` `break` lub `goto` słowa kluczowe w `__finally` / `finally` bloku ma niezdefiniowane zachowanie podczas nieprawidłowego zakończenia.|
|[C4533](../../error-messages/compiler-warnings/compiler-warning-level-1-c4533.md)|/we4533|Kod inicjujący zmienną nie zostanie wykonany.|
|[C4700](../../error-messages/compiler-warnings/compiler-warning-level-1-and-level-4-c4700.md)|/we4700|Użycie niezainicjowanej zmiennej lokalnej.|
|[C4703](../../error-messages/compiler-warnings/compiler-warning-level-4-c4703.md)|/we4703|Użycie potencjalnie niezainicjowanej zmiennej wskaźnika lokalnego.|
|[C4789](../../error-messages/compiler-warnings/compiler-warning-level-1-c4789.md)|/we4789|Przepełnienie buforu w przypadku korzystania z określonych funkcji języka C (CRT).|
|[C4995](../../error-messages/compiler-warnings/compiler-warning-level-3-c4995.md)|/we4995|Użycie funkcji oznaczonej za pomocą dyrektywy pragma [`deprecated`](../../preprocessor/deprecated-c-cpp.md) .|
|[C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)|/we4996|Użycie funkcji oznaczonej jako [`deprecated`](../../cpp/deprecated-cpp.md) .|

## <a name="runtime-checks"></a>Sprawdzenia środowiska uruchomieniowego

Gdy **`/sdl`** jest włączona, kompilator generuje kod, aby wykonać te testy w czasie wykonywania:

- Włącza tryb ścisły **`/GS`** wykrywania przepełnienia buforu w czasie wykonywania, który jest równoznaczny z kompilowaniem za pomocą `#pragma strict_gs_check(push, on)` .

- Wykonuje ograniczoną oczyszczanie wskaźnika. W wyrażeniach, które nie obejmują dereferencji i typów, które nie mają destruktora zdefiniowanego przez użytkownika, odwołania do wskaźnika są ustawiane jako nieprawidłowy adres po wywołaniu **`delete`** . Pozwala to zapobiec ponownemu używaniu przestarzałych odwołań do wskaźników.

- Wykonuje inicjalizację wskaźnika elementu członkowskiego klasy. Automatycznie inicjuje składowe klasy typu wskaźnika do **`nullptr`** tworzenia wystąpienia obiektu (przed uruchomieniem konstruktora). Pozwala to zapobiec użyciu niezainicjowanych wskaźników, które Konstruktor nie inicjuje jawnie. Inicjalizacja wskaźnika elementu członkowskiego wygenerowanego przez kompilator jest wywoływana tak długo, jak:

  - Obiekt nie jest przydzielony przy użyciu niestandardowego (zdefiniowanego przez użytkownika)`operator new`

  - Obiekt nie jest przydzielony jako część tablicy (na przykład `new A[x]` )

  - Klasa nie jest zarządzana ani zaimportowana

  - Klasa ma zdefiniowany przez użytkownika Konstruktor domyślny.

  Aby można było zainicjować za pomocą funkcji inicjowania klasy generowanej przez kompilator, element członkowski musi być wskaźnikiem, a nie właściwością ani stałą.

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [ostrzeżenia,/SDL i ulepszanie wykrywania zmiennej niezainicjowanej](https://cloudblogs.microsoft.com/microsoftsecure/2012/06/06/warnings-sdl-and-improving-uninitialized-variable-detection/).

#### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz folder **C/C++** .

1. Na stronie **Ogólne** wybierz opcję z listy rozwijanej **testy SDL** .

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
