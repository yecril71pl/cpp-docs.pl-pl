---
title: 'główne: uruchamianie programu | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- vc.main.startup
- _tmain
dev_langs:
- C++
helpviewer_keywords:
- program startup [C++]
- entry points, program
- wmain function
- _tmain function
- startup code, main function
- main function, program startup
ms.assetid: f9581cd6-93f7-4bcd-99ec-d07c3c107dd4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4ac33b9c7cbcc20f3cea55e73a0c079a21a068a9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46086060"
---
# <a name="main-program-startup"></a>main: uruchamianie programu

Specjalną funkcję o nazwie **głównego** jest punktem początkowym wykonanie wszystkich programów C i C++. Jeśli jesteś pisanie kodu, która jest zgodna z modelu programowania Unicode, możesz użyć `wmain`, która jest wersją znaków dwubajtowych z **głównego**.

**Głównego** funkcja nie jest wstępnie zdefiniowana przez kompilator. Wymagane jest podanie tekstu programu.

Składnia deklaracji **głównego** jest

```cpp
int main();
```

lub, opcjonalnie,

```cpp
int main(int argc, char *argv[], char *envp[]);
```

## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft

Składnia deklaracji `wmain` jest następująca:

```cpp
int wmain( );
```

lub, opcjonalnie,

```cpp
int wmain(int argc, wchar_t *argv[], wchar_t *envp[]);
```

Można również użyć `_tmain`, która została zdefiniowana w TCHAR.h. `_tmain` jest rozpoznawana jako **głównego** , chyba że _UNICODE zdefiniowano. W takim przypadku `_tmain` jest rozpoznawana jako `wmain`.

Alternatywnie **głównego** i `wmain` funkcje mogą być zadeklarowane jako zwracanie **void** (nie zwraca wartości). Jeśli zadeklarujesz **głównego** lub `wmain` powrotu **void**, nie można zwrócić kod wyjścia procesu nadrzędnego lub systemu operacyjnego za pomocą [zwracają](../cpp/return-statement-in-program-termination-cpp.md) instrukcji. Do zwrócenia wyjście kodu, gdy **głównego** lub `wmain` jest zadeklarowany jako **void**, należy użyć [wyjść](../cpp/exit-function.md) funkcji.

**END specyficzny dla Microsoft**

Typy dla `argc` i `argv` są definiowane przez język. Nazwy `argc`, `argv`, i `envp` są tradycyjne, ale nie są wymagane przez kompilator. Aby uzyskać więcej informacji i obejrzeć przykład, zobacz [definicje argumentu](../cpp/argument-definitions.md).

## <a name="see-also"></a>Zobacz także

[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[Korzystanie z wmain zamiast main](../cpp/using-wmain-instead-of-main.md)<br/>
[Ograniczenia funkcji main](../cpp/main-function-restrictions.md)<br/>
[Analizowanie argumentów wiersza polecenia języka C++](../cpp/parsing-cpp-command-line-arguments.md)