---
title: "Kompilatora (poziom 1) ostrzeżenie C4953 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4953
dev_langs: C++
helpviewer_keywords: C4953
ms.assetid: 3c4f6ac6-3976-41ab-8a27-3c41d7472ea7
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 807e091838db20fdcf66a74fe3050cf192fab1e3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4953"></a>Kompilator C4953 ostrzegawcze (poziom 1)
Element Wbudowywany "function" został wyedytowany od profil, który zebrania danych profilu dane nie zostały użyte  
  
 Korzystając z [/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md), kompilator wykryto moduł wejściowy kompilowanej po `/LTCG:PGINSTRUMENT` i ma funkcję (***funkcja***) który był edytowany i gdzie zidentyfikowanych uruchamia istniejącego testu Funkcja jako potencjalny ze śródwierszowaniem. Jednak w związku z tym ponownej kompilacji modułu, funkcja nie będzie już kandydatem do ze śródwierszowaniem.  
  
 To ostrzeżenie ma charakter informacyjny. Aby usunąć to ostrzeżenie, uruchom `/LTCG:PGINSTRUMENT`, powtórz test wszystkie działa, a następnie uruchom `/LTCG:PGOPTIMIZE`.  
  
 To ostrzeżenie będzie zastąpiony z powodu błędu, jeśli `/LTCG:PGOPTIMIZE` została użyta.