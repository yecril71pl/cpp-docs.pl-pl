---
title: 'main: uruchamianie programu'
ms.date: 11/04/2016
f1_keywords:
- vc.main.startup
- _tmain
helpviewer_keywords:
- program startup [C++]
- entry points, program
- wmain function
- _tmain function
- startup code, main function
- main function, program startup
ms.assetid: f9581cd6-93f7-4bcd-99ec-d07c3c107dd4
ms.openlocfilehash: 29e1b77c2e36c66e4e6fc4ec30a73af4d57654a0
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857440"
---
# <a name="main-program-startup"></a>main: uruchamianie programu

Funkcja specjalna o nazwie **Main** jest punktem początkowym wykonywania dla wszystkich języków C i C++ programów. Jeśli piszesz kod, który jest zgodny z modelem programowania Unicode, możesz użyć `wmain`, który jest wersją typu szerokiego **znaku.**

Funkcja **Main** nie jest wstępnie zdefiniowana przez kompilator. Musi być podana w tekście programu.

Składnia deklaracji dla **Main** to

```cpp
int main();
```

lub opcjonalnie,

```cpp
int main(int argc, char *argv[], char *envp[]);
```

**Microsoft Specific**

Składnia deklaracji dla `wmain` jest następująca:

```cpp
int wmain( );
```

lub opcjonalnie,

```cpp
int wmain(int argc, wchar_t *argv[], wchar_t *envp[]);
```

Można również użyć `_tmain`, który jest zdefiniowany w używanie TCHAR. h. `_tmain` jest rozpoznawana jako **Main** , chyba że _UNICODE jest zdefiniowany. W takim przypadku `_tmain` jest rozpoznawana jako `wmain`.

Alternatywnie można zadeklarować funkcje **Main** i `wmain` jako zwracające **typ void** (brak wartości zwracanej). Jeśli zadeklarujesz **Main** lub `wmain` jako zwraca **void**, nie można zwrócić kodu zakończenia do procesu nadrzędnego lub systemu operacyjnego za pomocą instrukcji [Return](../cpp/return-statement-in-program-termination-cpp.md) . Aby zwrócić kod zakończenia, gdy **główny** lub `wmain` jest zadeklarowany jako **void**, należy użyć funkcji [Exit](../cpp/exit-function.md) .

**ZAKOŃCZENIE określonych przez firmę Microsoft**

Typy dla `argc` i `argv` są definiowane przez język. Nazwy `argc`, `argv`i `envp` są tradycyjne, ale nie są wymagane przez kompilator. Aby uzyskać więcej informacji i zapoznać się z przykładem, zobacz [definicje argumentów](../cpp/argument-definitions.md).

## <a name="see-also"></a>Zobacz także

[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[Korzystanie z wmain zamiast main](../cpp/using-wmain-instead-of-main.md)<br/>
[Ograniczenia funkcji main](../cpp/main-function-restrictions.md)<br/>
[Analizowanie argumentów wiersza polecenia języka C++](../cpp/parsing-cpp-command-line-arguments.md)
