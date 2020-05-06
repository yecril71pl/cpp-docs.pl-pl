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
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62232819"
---
# <a name="naked-functions"></a>Funkcje Naked

**Specyficzne dla firmy Microsoft**

Atrybut `naked` klasy magazynowania to specyficzne dla firmy Microsoft rozszerzenie języka C. W przypadku funkcji zadeklarowanych `naked` z atrybutem klasy magazynowania kompilator generuje kod bez kodu prologu i epilogu. Za pomocą tej funkcji można napisać własne sekwencje kodu prologu/epilogu przy użyciu kodu asemblera wbudowanego. Wbudowane funkcje są szczególnie przydatne podczas pisania sterowników urządzeń wirtualnych.

Ponieważ `naked` atrybut ma zastosowanie tylko do definicji funkcji i nie jest modyfikatorem typu, funkcja bezużytecznych użyj składni atrybutów rozszerzonych, opisanej w temacie [rozszerzone atrybuty klasy magazynu](../c-language/c-extended-storage-class-attributes.md).

W poniższym przykładzie zdefiniowano funkcję z `naked` atrybutem:

```
__declspec( naked ) int func( formal_parameters )
{
   /* Function body */
}
```

Lub alternatywnie:

```
#define Naked   __declspec( naked )

Naked int func( formal_parameters )
{
   /* Function body */
}
```

Ten `naked` atrybut ma wpływ tylko na charakter generowania kodu kompilatora dla sekwencji Prolog i epilogu funkcji. Nie ma to wpływu na kod, który jest generowany do wywoływania takich funkcji. W `naked` ten sposób atrybut nie jest uważany za część typu funkcji, a wskaźniki funkcji nie mogą mieć `naked` atrybutu. Ponadto nie można `naked` zastosować atrybutu do definicji danych. Na przykład poniższy kod generuje błędy:

```
__declspec( naked ) int i;  /* Error--naked attribute not */
                            /* permitted on data declarations. */
```

`naked` Atrybut jest istotny tylko dla definicji funkcji i nie może być określony w prototypie funkcji. Następująca deklaracja generuje błąd kompilatora:

```
__declspec( naked ) int func();   /* Error--naked attribute not */
                     /* permitted on function declarations.    */   \
```

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[Definicje funkcji języka C](../c-language/c-function-definitions.md)
