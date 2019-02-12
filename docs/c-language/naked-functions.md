---
title: Funkcje Naked
ms.date: 11/04/2016
helpviewer_keywords:
- naked functions
- functions [C++], naked
- prolog code
- epilog code
ms.assetid: 2543c8af-00d4-4a2a-8a87-e746da1f9929
ms.openlocfilehash: b752dd6fa378bc1275e8a7da90420aa2b8247e4e
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152199"
---
# <a name="naked-functions"></a>Funkcje Naked

**Microsoft Specific**

`naked` Atrybuty klasy magazynu jest rozszerzeniem specyficzne dla firmy Microsoft dla języka C. Aby funkcje zadeklarowane za pomocą `naked` atrybuty klasy magazynu, kompilator generuje kod bez konieczności pisania kodu prologu i epilogu. Ta funkcja służy do pisania własnych sekwencji kodu prologu/epilogu przy użyciu kodu asemblera wbudowanego. Funkcji "naked" są szczególnie przydatne w pisaniu sterowniki urządzeń wirtualnych.

Ponieważ `naked` atrybutu, dotyczy tylko definicja funkcji i nie jest modyfikatora typu, funkcji "naked" należy użyć składni atrybutów rozszerzonych, opisanego w [rozszerzone atrybuty klasy magazynowania](../c-language/c-extended-storage-class-attributes.md).

Poniższy przykład definiuje funkcję za pomocą `naked` atrybutu:

```
__declspec( naked ) int func( formal_parameters )
{
   /* Function body */
}
```

Lub też:

```
#define Naked   __declspec( naked )

Naked int func( formal_parameters )
{
   /* Function body */
}
```

`naked` Atrybut ma wpływ jedynie charakter generowania kodu kompilator sekwencji prologu i epilogu funkcji. Nie ma wpływu na kod, który jest generowany w przypadku wywołania tych funkcji. W efekcie `naked` atrybut nie jest uważany za część typu funkcji i wskaźników do funkcji nie może mieć `naked` atrybutu. Ponadto `naked` atrybutu nie można zastosować do definicji danych. Na przykład poniższy kod generuje błędy:

```
__declspec( naked ) int i;  /* Error--naked attribute not */
                            /* permitted on data declarations. */
```

`naked` Atrybut ma zastosowanie tylko do definicji funkcji i nie można określić w prototypu funkcji. Następująca deklaracja generuje błąd kompilatora:

```
__declspec( naked ) int func();   /* Error--naked attribute not */
                     /* permitted on function declarations.    */   \
```

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Definicje funkcji języka C](../c-language/c-function-definitions.md)
