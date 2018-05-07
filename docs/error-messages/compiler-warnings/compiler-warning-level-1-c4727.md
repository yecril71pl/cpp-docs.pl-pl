---
title: Kompilatora (poziom 1) ostrzeżenie C4727 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4727
dev_langs:
- C++
helpviewer_keywords:
- C4727
ms.assetid: 991b0087-3a50-40f5-9cdb-cdc367cd472c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c92e42fe275f821e333a0f04a116034a5bb849a1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4727"></a>Kompilator C4727 ostrzegawcze (poziom 1)
"PCH o nazwie pch_file z tą samą sygnaturą czasową w obj_file_1 i obj_file_2.  Za pomocą pierwszego układu PCH.  
  
 C4727 występuje podczas kompilowania wielu jednostki kompilacji z **/Yc**, i gdy kompilator mógł Oznacz wszystkie pliki .obj z tą samą sygnaturą czasową .pch.  
  
 Aby rozwiązać, skompilować jeden plik źródłowy z **/Yc /c** (tworzy pch), i innych oddzielnie kompilacji z **/Yu /c** (używa pch), następnie połącz je.  
  
 Jeśli więc jest następujące i generuje C4727:  
  
 **Cl/CLR /GL a.cpp b.cpp c.cpp /Ycstdafx.h**  
  
 Użytkownik będzie należy zamiast tego:  
  
 **Cl/CLR /GL a.cpp /Ycstdafx.h /c**  
  
 **Cl/CLR /GL b.cpp c.cpp /Yustdafx.h/Link a.obj**  
  
 Aby uzyskać więcej informacji, zobacz artykuł  
  
-   [/Yc (Utwórz prekompilowany plik nagłówka)](../../build/reference/yc-create-precompiled-header-file.md)  
  
-   [/Yu (Korzystaj z prekompilowanego pliku nagłówka)](../../build/reference/yu-use-precompiled-header-file.md)