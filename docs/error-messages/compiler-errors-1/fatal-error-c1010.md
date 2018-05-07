---
title: Błąd krytyczny C1010 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1010
dev_langs:
- C++
helpviewer_keywords:
- C1010
ms.assetid: dfd035f1-a7a2-40bc-bc92-dc4d7f456767
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bf8af35b28cfa02bd2723ff3c78db04a27cc39ba
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="fatal-error-c1010"></a>Błąd krytyczny C1010
Nieoczekiwany koniec pliku podczas wyszukiwania prekompilowanego nagłówka. Czy zapomniano dodać "#include nazwę" do Twojego źródła?  
  
 Określony za pomocą plików dołączanych [/Yu](../../build/reference/yu-use-precompiled-header-file.md) nie znajduje się w pliku źródłowym.  Ta opcja jest włączona domyślnie w większości typy projektów Visual C++ i "stdafx.h" jest domyślnie Dołącz plik określony przez tę opcję.  
  
 W środowisku Visual Studio użyj jednej z następujących metod Aby rozwiązać ten problem:  
  
-   Jeśli nie używasz prekompilowanych nagłówków w projekcie, ustaw **Utwórz/Użyj Prekompilowanego nagłówka** właściwości pliki źródłowe do **nie przy użyciu prekompilowanych nagłówków**. Aby ustawić tę opcję kompilatora, wykonaj następujące kroki:  
  
    1.  W okienku Eksplorator rozwiązań projektu, kliknij prawym przyciskiem myszy nazwę projektu, a następnie kliknij przycisk **właściwości**.  
  
    2.  W okienku po lewej stronie kliknij **C/C++** folderu.  
  
    3.  Kliknij przycisk **prekompilowanych nagłówków** węzła.  
  
    4.  W okienku po prawej stronie kliknij **Utwórz/Użyj Prekompilowanego nagłówka**, a następnie kliknij przycisk **nie przy użyciu prekompilowanych nagłówków**.  
  
-   Upewnij się, że masz nie mogą przypadkowo usunięty, zmieniono jego nazwę lub usunąć plik nagłówka (domyślnie stdafx.h) z bieżącego projektu. Ten plik również musi być umieszczony przed innymi kodu w plikach źródłowych przy użyciu **#include "stdafx.h"**. (Ten plik nagłówka jest określony jako **Utwórz/Użyj PCH za pośrednictwem pliku** właściwości projektu)