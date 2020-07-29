---
title: naked (C++)
ms.date: 11/04/2016
f1_keywords:
- naked_cpp
helpviewer_keywords:
- __declspec keyword [C++], naked
- naked __declspec keyword
ms.assetid: 69723241-05e1-439b-868e-20a83a16ab6d
ms.openlocfilehash: cff2455608966886e9c5b07039dff439538caefe
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227338"
---
# <a name="naked-c"></a>naked (C++)

**Specyficzne dla firmy Microsoft**

W przypadku funkcji zadeklarowanych za pomocą **`naked`** atrybutu kompilator generuje kod bez kodu prologu i epilogu. Za pomocą tej funkcji można napisać własne sekwencje kodu prologu/epilogu przy użyciu kodu asemblera wbudowanego. Wbudowane funkcje są szczególnie przydatne podczas pisania sterowników urządzeń wirtualnych.  Należy zauważyć, że **`naked`** atrybut jest prawidłowy tylko w architekturze x86 i ARM i nie jest dostępny w architekturze x64.

## <a name="syntax"></a>Składnia

```
__declspec(naked) declarator
```

## <a name="remarks"></a>Uwagi

Ponieważ **`naked`** atrybut ma zastosowanie tylko do definicji funkcji i nie jest modyfikatorem typu, funkcje wykorzystające muszą używać składni atrybutów rozszerzonych i słowa kluczowego [__declspec](../cpp/declspec.md) .

Kompilator nie może wygenerować wbudowanej funkcji dla funkcji oznaczonej atrybutem owies, nawet jeśli funkcja jest również oznaczona za pomocą słowa kluczowego [__forceinline](inline-functions-cpp.md) .

Kompilator generuje błąd, jeśli **`naked`** atrybut jest stosowany do elementów innych niż definicja metody nienależącej do elementu członkowskiego.

## <a name="examples"></a>Przykłady

Ten kod definiuje funkcję z **`naked`** atrybutem:

```
__declspec( naked ) int func( formal_parameters ) {}
```

Alternatywnie:

```
#define Naked __declspec( naked )
Naked int func( formal_parameters ) {}
```

Ten **`naked`** atrybut ma wpływ tylko na charakter generowania kodu kompilatora dla sekwencji Prolog i epilogu funkcji. Nie ma to wpływu na kod, który jest generowany do wywoływania takich funkcji. W ten sposób **`naked`** atrybut nie jest uważany za część typu funkcji, a wskaźniki funkcji nie mogą mieć **`naked`** atrybutu. Ponadto **`naked`** nie można zastosować atrybutu do definicji danych. Na przykład ten przykładowy kod generuje błąd:

```
__declspec( naked ) int i;
// Error--naked attribute not permitted on data declarations.
```

**`naked`** Atrybut jest istotny tylko dla definicji funkcji i nie może być określony w prototypie funkcji. Na przykład ta deklaracja generuje błąd kompilatora:

```
__declspec( naked ) int func();  // Error--naked attribute not permitted on function declarations
```

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[__declspec](../cpp/declspec.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[Wywołania funkcji bez nadruku](../cpp/naked-function-calls.md)
