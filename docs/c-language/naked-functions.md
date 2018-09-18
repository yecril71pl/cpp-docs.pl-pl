---
title: Funkcje naked | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- naked functions
- functions [C++], naked
- prolog code
- epilog code
ms.assetid: 2543c8af-00d4-4a2a-8a87-e746da1f9929
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 134584ed1acd502ecbf74fe755850761df8c08e1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46061490"
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

## <a name="see-also"></a>Zobacz też

[Definicje funkcji języka C](../c-language/c-function-definitions.md)