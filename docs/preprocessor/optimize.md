---
title: optymalizuj
ms.date: 11/04/2016
f1_keywords:
- vc-pragma.optimize
- optimize_CPP
helpviewer_keywords:
- pragmas, optimize
- optimize pragma
ms.assetid: cb13c1cc-186a-45bc-bee7-95a8de7381cc
ms.openlocfilehash: 9f5240fc59f59a71ddb3d18b67fadf3463a0d1ea
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59035403"
---
# <a name="optimize"></a>optymalizuj

Określa optymalizacje wykonywane na podstawie funkcji przez funkcję.

## <a name="syntax"></a>Składnia

```
#pragma optimize( "[optimization-list]", {on | off} )
```

## <a name="remarks"></a>Uwagi

**Zoptymalizować** pragma musi znajdować się poza funkcją i zaczyna obowiązywać przy pierwszej funkcji zdefiniowanych po pragmy jest widoczny. *Na* i *poza* argumenty Włącz opcje określone w *listy optymalizacji* lub wyłączyć.

*Listy optymalizacji* może być zero lub jeden z parametrów pokazano w poniższej tabeli.

### <a name="parameters-of-the-optimize-pragma"></a>Parametry optymalizacji Pragma

|Parametry|Typ optymalizacji|
|--------------------|--------------------------|
|*g*|Włącz optymalizacje globalne.|
|*s* lub *t*|Określ krótki i szybkie sekwencji kodu maszynowego.|
|*t*|Generowanie wskaźników ramek na stosie program.|

Są to tych samych liter, w ramach [/O](../build/reference/o-options-optimize-code.md) opcje kompilatora. Na przykład, następujące pragmy jest odpowiednikiem `/Os` — opcja kompilatora:

```
#pragma optimize( "ts", on )
```

Za pomocą **zoptymalizować** dyrektywę pusty ciąg (**""**) jest specjalną forma dyrektywy:

Zastosowania *poza* parametru go włącza optymalizacje *g*, *s*, *t*, i *y*, wyłącz.

Kiedy używasz *na* parametru resetuje Optymalizacje te, które określono [/O](../build/reference/o-options-optimize-code.md) — opcja kompilatora.

```
#pragma optimize( "", off )
.
.
.
#pragma optimize( "", on )
```

## <a name="see-also"></a>Zobacz także

[Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)