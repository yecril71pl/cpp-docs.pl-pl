---
title: Kompilowanie programu opartego na atrybutach | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- tlb files
- MIDL
- MIDL, linker output
- IDL files
- tlb files, building attributed programs
- .tlb files, building attributed programs
- IDL files, building
- attributes [C++], building type libraries and .idl files
- .tlb files
- .idl files, building
- type libraries, linker options for building
ms.assetid: 04997b5f-bf2c-46ec-b868-c4adebbef5f4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7909884a355ccad5e1bf9d18a38dd3e4690296ee
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42587510"
---
# <a name="building-an-attributed-program"></a>Kompilowanie programu opartego na atrybutach

Po atrybuty Visual C++ są umieszczane w kodzie źródłowym, może być kompilator języka Visual C++, aby wygenerować plik biblioteki i .idl typu dla Ciebie. Konsolidator następujące opcje pomagają tworzyć plików .tlb i .idl:

- [/ IDLOUT](../build/reference/idlout-name-midl-output-files.md)

- [/ IGNOREIDL](../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)

- [/ MIDL](../build/reference/midl-specify-midl-command-line-options.md)

- [/ TLBOUT](../build/reference/tlbout-name-dot-tlb-file.md)

Niektóre projekty zawierają wiele plików .idl niezależne. Są one używane do utworzenia dwóch lub więcej plików .tlb i opcjonalnie powiązać je w bloku zasobów. W tym scenariuszu nie jest obecnie obsługiwane w programie Visual C++.

Ponadto konsolidator Visual C++ zwróci wszystkie informacje związane z IDL atrybut do jednego pliku MIDL. Będzie sposób generowania dwie biblioteki typów z pojedynczego projektu.

## <a name="see-also"></a>Zobacz też

[Pojęcia](../windows/attributed-programming-concepts.md)