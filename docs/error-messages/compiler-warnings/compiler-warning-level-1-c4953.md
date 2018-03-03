---
title: "Kompilatora (poziom 1) ostrzeżenie C4953 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4953
dev_langs:
- C++
helpviewer_keywords:
- C4953
ms.assetid: 3c4f6ac6-3976-41ab-8a27-3c41d7472ea7
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c330076e7c0b4ff6daded94ef5fc038bd9dad759
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4953"></a>Kompilator C4953 ostrzegawcze (poziom 1)
Element Wbudowywany "function" został wyedytowany od profil, który zebrania danych profilu dane nie zostały użyte  
  
 Korzystając z [/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md), kompilator wykryto moduł wejściowy kompilowanej po `/LTCG:PGINSTRUMENT` i ma funkcję (***funkcja***) który był edytowany i gdzie zidentyfikowanych uruchamia istniejącego testu Funkcja jako potencjalny ze śródwierszowaniem. Jednak w związku z tym ponownej kompilacji modułu, funkcja nie będzie już kandydatem do ze śródwierszowaniem.  
  
 To ostrzeżenie ma charakter informacyjny. Aby usunąć to ostrzeżenie, uruchom `/LTCG:PGINSTRUMENT`, powtórz test wszystkie działa, a następnie uruchom `/LTCG:PGOPTIMIZE`.  
  
 To ostrzeżenie będzie zastąpiony z powodu błędu, jeśli `/LTCG:PGOPTIMIZE` została użyta.