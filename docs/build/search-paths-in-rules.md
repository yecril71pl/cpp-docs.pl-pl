---
title: Ścieżki wyszukiwania w regułach | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- search paths in NMAKE inference rules
- inference rules in NMAKE
- rules, inference
ms.assetid: 38feded6-536d-425d-bf40-fff3173a5506
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c96ee89367c3ac289dffde9029cb2b5d3cdc3e89
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45703979"
---
# <a name="search-paths-in-rules"></a>Ścieżki wyszukiwania w zasadach

```
{frompath}.fromext{topath}.toext:
   commands
```

## <a name="remarks"></a>Uwagi

Reguła wnioskowania dotyczy zależność, tylko wtedy, gdy ścieżki określane w zależność dokładnie odpowiadać ścieżki w regule wnioskowania. Określ katalog zależnego w *frompath* i katalog docelowy w *topath*; spacje nie są dozwolone. Określ tylko jedną ścieżkę dla każdego rozszerzenia. Ścieżki na jedno rozszerzenie wymaga ścieżki na drugi. Aby określić bieżącego katalogu, użyj kropki (.) lub pustych nawiasów klamrowych ({}). Makra mogą reprezentować *frompath* i *topath*; są one wywoływane podczas przetwarzania wstępnego.

## <a name="example"></a>Przykład

### <a name="code"></a>Kod

```
{dbi\}.cpp{$(ODIR)}.obj::
        $(CC) $(CFLAGS) $(YUDBI) $<

{ilstore\}.cpp{$(ODIR)}.obj::
        $(CC) $(CFLAGS) $<

{misc\}.cpp{$(ODIR)}.obj::
        $(CC) $(CFLAGS) $(YUPDB) $<

{misc\}.c{$(ODIR)}.obj::
        $(CC) $(CFLAGS) $<

{msf\}.cpp{$(ODIR)}.obj::
        $(CC) $(CFLAGS) $<

{bsc\}.cpp{$(ODIR)}.obj::
        $(CC) $(CFLAGS) $(YUPDB) $<

{mre\}.cpp{$(ODIR)}.obj::
        $(CC) $(CFLAGS) $(YUPDB) $<

{namesrvr\}.cpp{$(ODIR)}.obj::
        $(CC) $(CFLAGS) $(YUPDB) $<

{src\cvr\}.cpp{$(ODIR)}.obj::
        $(CC) $(CFLAGS) $<
```

## <a name="see-also"></a>Zobacz też

[Definiowanie zasady](../build/defining-a-rule.md)