---
title: Kompilatora (poziom 1) ostrzeżenie C4953 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4953
dev_langs:
- C++
helpviewer_keywords:
- C4953
ms.assetid: 3c4f6ac6-3976-41ab-8a27-3c41d7472ea7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0af5a16ebbf7851eceb2f2cd355f953b14c4bd38
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33293065"
---
# <a name="compiler-warning-level-1-c4953"></a>Kompilator C4953 ostrzegawcze (poziom 1)
Element Wbudowywany "function" został wyedytowany od profil, który zebrania danych profilu dane nie zostały użyte  
  
 Korzystając z [/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md), kompilator wykryto moduł wejściowy kompilowanej po `/LTCG:PGINSTRUMENT` i ma funkcję (***funkcja***) który był edytowany i gdzie zidentyfikowanych uruchamia istniejącego testu Funkcja jako potencjalny ze śródwierszowaniem. Jednak w związku z tym ponownej kompilacji modułu, funkcja nie będzie już kandydatem do ze śródwierszowaniem.  
  
 To ostrzeżenie ma charakter informacyjny. Aby usunąć to ostrzeżenie, uruchom `/LTCG:PGINSTRUMENT`, powtórz test wszystkie działa, a następnie uruchom `/LTCG:PGOPTIMIZE`.  
  
 To ostrzeżenie będzie zastąpiony z powodu błędu, jeśli `/LTCG:PGOPTIMIZE` została użyta.