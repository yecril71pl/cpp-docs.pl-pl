---
title: Ostrzeżenie kompilatora (poziom 1) C4727
ms.date: 08/19/2019
f1_keywords:
- C4727
helpviewer_keywords:
- C4727
ms.assetid: 991b0087-3a50-40f5-9cdb-cdc367cd472c
ms.openlocfilehash: 1bcc029536d2602d50178d7148332b8371db3c7f
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630832"
---
# <a name="compiler-warning-level-1-c4727"></a>Ostrzeżenie kompilatora (poziom 1) C4727

"PCH o nazwie pch_file z tą samą sygnaturą czasową znaleziono w obj_file_1 i obj_file_2.  Przy użyciu pierwszego PCH.

> [!NOTE]
> W programie Visual Studio 2017 i starszych wersjach prekompilowanego nagłówka jest domyślnie wywoływana *stdafx. h* , a w programie Visual Studio 2019 i nowszych jest nazywana domyślnie *PCH. h* .

C4727 występuje podczas kompilowania wielu compilands z **/YC**i gdzie kompilator mógł oznaczyć wszystkie pliki. obj z tym samym znacznikiem czasu PCH.

Aby rozwiązać ten problem, Skompiluj jeden plik źródłowy z **/Yc/c** (tworzy pch), a pozostałe kompiluje z **/Yu/c** (używa pch), a następnie połącz je ze sobą.

Tak więc, jeśli wykonano następujące czynności i wygeneruje C4727:

::: moniker range="<=vs-2017"

**CL/CLR/GL a. cpp b. cpp c. cpp/Ycstdafx.h**

Zamiast tego należy wykonać następujące czynności:

**CL/CLR/GL a. cpp/Ycstdafx.h/c**

**CL/CLR/GL b. cpp c. cpp/Yustdafx.h. obj**

::: moniker-end

::: moniker range=">=vs-2019"

**CL/CLR/GL a. cpp b. cpp c. cpp/Ycpch.h**

Zamiast tego należy wykonać następujące czynności:

**CL/CLR/GL a. cpp/Ycpch.h/c**

**CL/CLR/GL b. cpp c. cpp/Yupch.h. obj**

::: moniker-end


Aby uzyskać więcej informacji, zobacz artykuł

- [/Yc (Utwórz prekompilowany plik nagłówka)](../../build/reference/yc-create-precompiled-header-file.md)

- [/Yu (Korzystaj z prekompilowanego pliku nagłówka)](../../build/reference/yu-use-precompiled-header-file.md)