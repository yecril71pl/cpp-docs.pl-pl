---
title: naked (C++)
ms.date: 11/04/2016
f1_keywords:
- naked_cpp
helpviewer_keywords:
- __declspec keyword [C++], naked
- naked __declspec keyword
ms.assetid: 69723241-05e1-439b-868e-20a83a16ab6d
ms.openlocfilehash: 951760d7f9566c084bbe3d5a574d006020576c61
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50478380"
---
# <a name="naked-c"></a>naked (C++)

**Microsoft Specific**

Aby funkcje zadeklarowane za pomocą **"naked"** atrybutu, kompilator generuje kod bez konieczności pisania kodu prologu i epilogu. Ta funkcja służy do pisania własnych sekwencji kodu prologu/epilogu przy użyciu kodu asemblera wbudowanego. Funkcji "naked" są szczególnie przydatne w pisaniu sterowniki urządzeń wirtualnych.  Należy pamiętać, że **"naked"** atrybut jest prawidłowy tylko w x86 i ARM i nie jest dostępny na x64.

## <a name="syntax"></a>Składnia

```
__declspec(naked) declarator
```

## <a name="remarks"></a>Uwagi

Ponieważ **"naked"** atrybutu, dotyczy tylko definicja funkcji i nie jest modyfikatora typu, funkcji "naked" należy użyć składni atrybutów rozszerzonych i [__declspec](../cpp/declspec.md) — słowo kluczowe.

Kompilator nie może wygenerować wbudowanej funkcji dla funkcji z atrybutem "naked", nawet wtedy, gdy funkcja jest również oznaczona za pomocą [__forceinline](inline-functions-cpp.md) — słowo kluczowe.

Kompilator generuje błąd, jeśli **"naked"** atrybut jest stosowany do coś innego niż definicji metody nieczłonkowską.

## <a name="examples"></a>Przykłady

Ten kod definiuje funkcję za pomocą **"naked"** atrybutu:

```
__declspec( naked ) int func( formal_parameters ) {}
```

Lub też:

```
#define Naked __declspec( naked )
Naked int func( formal_parameters ) {}
```

**"Naked"** atrybut ma wpływ jedynie charakter generowania kodu kompilator sekwencji prologu i epilogu funkcji. Nie ma wpływu na kod, który jest generowany w przypadku wywołania tych funkcji. W efekcie **"naked"** atrybut nie jest uważany za część typu funkcji i wskaźników do funkcji nie może mieć **"naked"** atrybutu. Ponadto **"naked"** atrybutu nie można zastosować do definicji danych. Na przykład ten przykładowy kod generuje błąd:

```
__declspec( naked ) int i;
// Error--naked attribute not permitted on data declarations.
```

**"Naked"** atrybut ma zastosowanie tylko do definicji funkcji i nie można określić w prototypu funkcji. Na przykład tej deklaracji generuje błąd kompilatora:

```
__declspec( naked ) int func();  // Error--naked attribute not permitted on function declarations
```

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[__declspec](../cpp/declspec.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[Wywołania funkcji Naked](../cpp/naked-function-calls.md)