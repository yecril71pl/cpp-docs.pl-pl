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
ms.openlocfilehash: 25127377f20de3cb7c7b55e275692eefbf077067
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="search-paths-in-rules"></a>Ścieżki wyszukiwania w zasadach
```  
{frompath}.fromext{topath}.toext:  
   commands  
```  
  
## <a name="remarks"></a>Uwagi  
 Reguła wnioskowania dotyczy zależność tylko wtedy, gdy ścieżek określonych w zależności dokładnie zgodne ścieżki reguły wnioskowania. Określ katalog zależnego w *frompath* i katalog docelowy w *topath*; może nie zawierać spacje. Określ tylko jedną ścieżkę dla każdego rozszerzenia. Ścieżka na jedno rozszerzenie wymaga ścieżki z drugiej strony. Aby określić bieżącego katalogu, użyj kropki (.) lub pustymi nawiasami klamrowymi ({}). Makra może reprezentować *frompath* i *topath*; są one wywoływane podczas przetwarzania wstępnego.  
  
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