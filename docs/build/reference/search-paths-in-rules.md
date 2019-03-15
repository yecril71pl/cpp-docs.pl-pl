---
title: Ścieżki wyszukiwania w zasadach
ms.date: 11/04/2016
helpviewer_keywords:
- search paths in NMAKE inference rules
- inference rules in NMAKE
- rules, inference
ms.assetid: 38feded6-536d-425d-bf40-fff3173a5506
ms.openlocfilehash: eab6e9d32940aaf5729ce82c4e8258a3a3132208
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823886"
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

## <a name="see-also"></a>Zobacz także

[Definiowanie zasady](defining-a-rule.md)
