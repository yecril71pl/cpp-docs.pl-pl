---
title: Błąd PRJ0006 kompilacji projektu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0006
dev_langs:
- C++
helpviewer_keywords:
- PRJ0006
ms.assetid: ce092be4-1652-414f-8cb5-b97ef5841f89
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 151c22bf13c13de21e89a5c96185cf1c4c1ca349
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33317482"
---
# <a name="project-build-error-prj0006"></a>Błąd PRJ0006 kompilacji projektu
Nie można otworzyć pliku tymczasowego 'Plik'. Upewnij się, że plik istnieje i że katalog jest nie zabezpieczony przed zapisem.  
  
 Visual C++ nie można utworzyć pliku tymczasowego podczas procesu kompilacji. Powody mogą być następujące:  
  
-   Nie katalogu tymczasowego.  
  
-   Tylko do odczytu katalogu tymczasowego.  
  
-   Brak miejsca na dysku.  
  
-   $(IntDir) folder jest tylko do odczytu lub zawiera pliki tymczasowe, które są tylko do odczytu.  
  
 Ten błąd wystąpi następujący błąd PRJ0007: nie można utworzyć katalogu "katalog wyjściowy'. Błąd PRJ0007 oznacza, że nie można utworzyć katalogu $(IntDir), co oznacza tworzenie plików tymczasowo również zakończą się.  
  
 Pliki tymczasowe są tworzone przy każdym należy określić:  
  
-   Plik odpowiedzi.  
  
-   Niestandardowy krok kompilacji.  
  
-   Zdarzenia kompilacji.