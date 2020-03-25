---
title: naked (C++)
ms.date: 11/04/2016
f1_keywords:
- naked_cpp
helpviewer_keywords:
- __declspec keyword [C++], naked
- naked __declspec keyword
ms.assetid: 69723241-05e1-439b-868e-20a83a16ab6d
ms.openlocfilehash: cfe3631086515e4e31c7d4188d46e3a7440662b7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177953"
---
# <a name="naked-c"></a>naked (C++)

**Specyficzne dla firmy Microsoft**

W przypadku funkcji zadeklarowanych za pomocą atrybutu **owies** kompilator generuje kod bez kodu prologu i epilogu. Za pomocą tej funkcji można napisać własne sekwencje kodu prologu/epilogu przy użyciu kodu asemblera wbudowanego. Wbudowane funkcje są szczególnie przydatne podczas pisania sterowników urządzeń wirtualnych.  Należy zauważyć, że atrybut " **owies** " jest prawidłowy tylko w architekturze x86 i ARM i nie jest dostępny w architekturze x64.

## <a name="syntax"></a>Składnia

```
__declspec(naked) declarator
```

## <a name="remarks"></a>Uwagi

Ponieważ atrybut " **owies** " ma zastosowanie tylko do definicji funkcji i nie jest modyfikatorem typu, funkcja bez użycia musi używać składni atrybutów rozszerzonych i słowa kluczowego [__declspec](../cpp/declspec.md) .

Kompilator nie może wygenerować wbudowanej funkcji dla funkcji oznaczonej atrybutem owies, nawet jeśli funkcja jest również oznaczona za pomocą słowa kluczowego [__forceinline](inline-functions-cpp.md) .

Kompilator generuje błąd, jeśli atrybut " **owies** " jest stosowany do elementów innych niż definicja metody nienależącej do elementu członkowskiego.

## <a name="examples"></a>Przykłady

Ten kod definiuje funkcję z atrybutem **owies** :

```
__declspec( naked ) int func( formal_parameters ) {}
```

Alternatywnie:

```
#define Naked __declspec( naked )
Naked int func( formal_parameters ) {}
```

Atrybut **owies** ma wpływ tylko na charakter generowania kodu kompilatora dla sekwencji Prolog i epilogu funkcji. Nie ma to wpływu na kod, który jest generowany do wywoływania takich funkcji. W ten sposób atrybut **owies** nie jest uważany za część typu funkcji, a wskaźniki funkcji nie mogą mieć atrybutu **owies** . Ponadto atrybut **owies** nie może zostać zastosowany do definicji danych. Na przykład ten przykładowy kod generuje błąd:

```
__declspec( naked ) int i;
// Error--naked attribute not permitted on data declarations.
```

Atrybut " **owies** " ma zastosowanie tylko do definicji funkcji i nie może być określony w prototypie funkcji. Na przykład ta deklaracja generuje błąd kompilatora:

```
__declspec( naked ) int func();  // Error--naked attribute not permitted on function declarations
```

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[__declspec](../cpp/declspec.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[Wywołania funkcji Naked](../cpp/naked-function-calls.md)
