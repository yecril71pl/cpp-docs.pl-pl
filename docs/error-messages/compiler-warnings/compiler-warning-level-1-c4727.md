---
title: Kompilator ostrzeżenie (poziom 1) C4727
ms.date: 11/04/2016
f1_keywords:
- C4727
helpviewer_keywords:
- C4727
ms.assetid: 991b0087-3a50-40f5-9cdb-cdc367cd472c
ms.openlocfilehash: be1a248fc2709706e137b543344966735c19064e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50490574"
---
# <a name="compiler-warning-level-1-c4727"></a>Kompilator ostrzeżenie (poziom 1) C4727

"PCH o nazwie pch_file z tą samą sygnaturą czasową w obj_file_1 i obj_file_2.  Za pomocą pierwszego układu PCH.

C4727 występuje podczas kompilowania wielu compilands z **/Yc**, i gdzie kompilator można było oznaczyć wszystkie pliki .obj, z tą samą sygnaturą czasową .pch.

Aby rozwiązać problem, skompiluj jeden plik źródłowy przy użyciu **/Yc /c** (tworzy pch), i inne oddzielnie kompilacji z **/Yu /c** (używa pch), łączyć je ze sobą.

Jeśli więc zostały następujące i generuje C4727:

**Cl/CLR /GL a.cpp b.cpp c.cpp /Ycstdafx.h**

Jak w następujących zamiast tego:

**Cl/CLR /GL a.cpp /Ycstdafx.h /c**

**Cl/CLR /GL b.cpp c.cpp /Yustdafx.h/Link a.obj**

Aby uzyskać więcej informacji, zobacz artykuł

- [/Yc (Utwórz prekompilowany plik nagłówka)](../../build/reference/yc-create-precompiled-header-file.md)

- [/Yu (Korzystaj z prekompilowanego pliku nagłówka)](../../build/reference/yu-use-precompiled-header-file.md)