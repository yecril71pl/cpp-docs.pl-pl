---
title: /sdl (Włącz dodatkowe kontrole zabezpieczeń)
ms.date: 11/26/2018
f1_keywords:
- VC.Project.VCCLCompilerTool.SDLCheck
ms.assetid: 3dcf86a0-3169-4240-9f29-e04a9f535826
ms.openlocfilehash: 0618b796d492395c3e0e5413047ac0260082baff
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62318449"
---
# <a name="sdl-enable-additional-security-checks"></a>/sdl (Włącz dodatkowe kontrole zabezpieczeń)

Dodaje zalecane testy cykl projektowania zabezpieczeń (SDL). Testy te obejmują dodatkowych związanych z zabezpieczeniami ostrzeżenia jako błędy i funkcje dodatkowe bezpiecznego generowania kodu.

## <a name="syntax"></a>Składnia

```
/sdl[-]
```

## <a name="remarks"></a>Uwagi

**/ SDL** włącza nadzbiór kontrole zabezpieczeń linii bazowej, które są dostarczane przez [/GS](gs-buffer-security-check.md) i zastępuje **/GS-**. Domyślnie **/SDL** jest wyłączona. **Zgłaszanie** wyłącza dodatkowe kontrole zabezpieczeń.

## <a name="compile-time-checks"></a>Sprawdzanie w czasie kompilacji

**/ SDL** włącza te ostrzeżenia jako błędy:

|Ostrzeżenie włączone przez/SDL|Równoważne przełącznik wiersza polecenia|Opis|
|------------------------------|-------------------------------------|-----------------|
|[C4146](../../error-messages/compiler-warnings/compiler-warning-level-2-c4146.md)|/we4146|Jednoargumentowy minus operator została zastosowana do typu unsigned, co wynik bez znaku.|
|[C4308](../../error-messages/compiler-warnings/compiler-warning-level-2-c4308.md)|/we4308|Ujemne stałe całkowite skonwertowano na typ bez znaku, co w wyniku prawdopodobnie ta nie ma znaczenia.|
|[C4532](../../error-messages/compiler-warnings/compiler-warning-level-1-c4532.md)|/we4532|Korzystanie z `continue`, `break` lub `goto` słów kluczowych w `__finally` / `finally` bloku posiada niezdefiniowane zachowanie podczas Nienormalne zakończenie.|
|[C4533](../../error-messages/compiler-warnings/compiler-warning-level-1-c4533.md)|/we4533|Kod inicjowania zmiennej nie zostaną wykonane.|
|[C4700](../../error-messages/compiler-warnings/compiler-warning-level-1-and-level-4-c4700.md)|/we4700|Użycie niezainicjowanej zmiennej lokalnej.|
|[C4703](../../error-messages/compiler-warnings/compiler-warning-level-4-c4703.md)|/we4703|Użycie potencjalnie niezainicjowanej lokalnej zmiennej wskaźnikowej.|
|[C4789](../../error-messages/compiler-warnings/compiler-warning-level-1-c4789.md)|/we4789|Przepełnienie podczas korzystania z określonych funkcji wykonawczej (CRT) C buforu.|
|[C4995](../../error-messages/compiler-warnings/compiler-warning-level-3-c4995.md)|/we4995|Korzystanie z funkcji oznaczona za pomocą pragmy [przestarzałe](../../preprocessor/deprecated-c-cpp.md).|
|[C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)|/we4996|Korzystanie z funkcji oznaczone jako [przestarzałe](../../cpp/deprecated-cpp.md).|

## <a name="runtime-checks"></a>Testy środowiska uruchomieniowego

Gdy **/SDL** jest włączone, kompilator generuje kod do wykonywania tych sprawdzeń w czasie wykonywania:

- Włącza tryb strict **/GS** wykrywania przepełnienia buforu środowiska wykonawczego, odpowiednikiem kompilowania za pomocą `#pragma strict_gs_check(push, on)`.

- Wykonuje oczyszczania ograniczone wskaźnika. W wyrażeniach, które nie wymagają wyłuskań, i na typy, które mają nie destruktor zdefiniowany przez użytkownika, wskaźnik odwołania są ustawione na nie jest prawidłowym adresem po wywołaniu `delete`. Pomaga to zapobiec ponownemu użyciu starych wskaźnik odwołania.

- Wykonuje inicjowanie wskaźnika składowej klasy. Automatycznie inicjuje klasy elementy członkowskie typu wskaźnika do **nullptr** na tworzenia wystąpienia obiektu (przed uruchomieniem Konstruktora). Pozwala to zapobiec użycie niezainicjowanej wskaźników, które nie jawnie zainicjować konstruktora. Inicjowanie wskaźników generowanych przez kompilator składowej jest wywoływana tak długo, jak:

  - Obiekt nie jest przydzielony przy użyciu niestandardowego (zdefiniowane przez użytkownika) `operator new`

  - Obiekt nie jest przydzielony jako część tablicy (na przykład `new A[x]`)

  - Klasa nie jest zarządzany lub zaimportowany

  - Klasa ma Konstruktor zdefiniowany przez użytkownika.

  Mają być inicjowane przez funkcję inicjowania klasy generowane przez kompilator, członek musi być wskaźnikiem, a nie właściwości lub — stała.

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [ostrzeżenia, / SDL i poprawy niezainicjowanej zmiennej wykrywania](https://cloudblogs.microsoft.com/microsoftsecure/2012/06/06/warnings-sdl-and-improving-uninitialized-variable-detection/).

#### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **C/C++** folderu.

1. Na **ogólne** wybierz tę opcję z **sprawdzenia SDL** listy rozwijanej.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
