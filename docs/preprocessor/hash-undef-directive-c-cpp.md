---
title: '#undef — dyrektywa (C/C++)'
ms.date: 11/04/2016
f1_keywords:
- '#undef'
helpviewer_keywords:
- '#undef directive'
- undef directive (#undef)
- preprocessor, directives
ms.assetid: 88900e0e-2c19-4a63-b681-f3d3133c24ca
ms.openlocfilehash: 4f4f5ce244be6d7f4e13d7a2abc5d21232c08d9d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62409853"
---
# <a name="undef-directive-cc"></a>#undef — dyrektywa (C/C++)
Usuwa (jedno anulowanie definicji) nazwę wcześniej utworzone za pomocą `#define`.

## <a name="syntax"></a>Składnia

```
#undef
identifier
```

## <a name="remarks"></a>Uwagi

**#Undef** dyrektywa spowoduje usunięcie bieżącej definicji *identyfikator*. W związku z tym kolejne wystąpienia *identyfikator* są ignorowane przez preprocesor. Można usunąć definicji makra przy użyciu **#undef**, określ tylko makra *identyfikator* ; nie ma listy parametrów.

Można również zastosować **#undef** dyrektywę identyfikator, który nie ma poprzedniego definicji. Zapewnia to, że identyfikator jest niezdefiniowany. Wymiana makra nie jest wykonywana w ramach **#undef** instrukcji.

**#Undef** dyrektywy zwykle jest powiązany z `#define` dyrektywy do tworzenia regionu w programie źródłowym, w którym identyfikator ma specjalne znaczenie. Na przykład określoną funkcję program źródłowy można użyć stałych manifestu do definiowania wartości specyficzne dla środowiska, które nie dotyczą całego programu. **#Undef** dyrektywa działa także w przypadku `#if` dyrektywy do kontrolowania kompilacji warunkowej programu źródłowego. Zobacz [#if, #elif #else i #endif, dyrektywy](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md) Aby uzyskać więcej informacji.

W poniższym przykładzie **#undef** dyrektywy Usuwa definicje symboliczna stała i makra. Pamiętaj, że biorąc pod uwagę tylko identyfikator makra.

```
#define WIDTH 80
#define ADD( X, Y ) ((X) + (Y))
.
.
.
#undef WIDTH
#undef ADD
```

**Microsoft Specific**

Makra mogą być niezdefiniowana z wiersza polecenia przy użyciu `/U` opcji, a po niej niezdefiniowanej nazwy makra. Efekt wydaniu tego polecenia jest równoważna z sekwencji `#undef` *Nazwa makra* instrukcji na początku pliku.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Dyrektywy preprocesora](../preprocessor/preprocessor-directives.md)