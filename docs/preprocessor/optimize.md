---
title: Optymalizowanie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.optimize
- optimize_CPP
dev_langs:
- C++
helpviewer_keywords:
- pragmas, optimize
- optimize pragma
ms.assetid: cb13c1cc-186a-45bc-bee7-95a8de7381cc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 98275f6e0a16c6d07b66ce592eb12b9391157653
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50069740"
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
|*y*|Generowanie wskaźników ramek na stosie program.|

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

## <a name="see-also"></a>Zobacz też

[Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)