---
title: dla Statement (C) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: for keyword [C]
ms.assetid: 560a8de4-19db-4868-9f18-dbe51b17900d
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 13d292cebbb8aa3aa6a65fbc41b8b38934732b5f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="for-statement-c"></a>for — instrukcja (C)
**Dla** instrukcji umożliwia Powtórz instrukcję lub instrukcja złożona określoną liczbę razy. Treść **dla** instrukcja jest wykonywana na zero lub więcej razy, aż opcjonalny warunek stanie się wartość false. Można użyć wyrażenia opcjonalne w **dla** instrukcji do inicjowania i zmień wartości podczas **dla** wykonywania w instrukcji.  
  
## <a name="syntax"></a>Składnia  
 *instrukcji iteracji*:  
 &nbsp;&nbsp;**Aby uzyskać** **(** *wyrażenie init*<sub>opt</sub> **;** *wyrażenia warunkowego*<sub>opt</sub> **;** *pętli wyrażenie*<sub>opt</sub> **)** *— instrukcja*  
  
 Wykonywanie **dla** instrukcji będzie kontynuowana w następujący sposób:  
  
1.  *Wyrażenie init*, jeśli istnieje, jest obliczane. To ustawienie określa inicjowania pętli. Nie podlega ograniczeniom typu *init wyrażenia*.  
  
2.  *Wyrażenia warunkowego*, jeśli istnieje, jest obliczane. To wyrażenie musi mieć typ arytmetyczny lub wskaźnikowy. Oceny przed każdej iteracji. Możliwe są trzy wyników:  
  
    -   Jeśli *wyrażenia warunkowego* jest **true** (niezerowej) *instrukcji* jest wykonywane; następnie *pętli wyrażenie*, jeśli istnieje, jest obliczane. *Pętli wyrażenie* jest oceniane po każdej iteracji. Nie podlega ograniczeniom w jego typie. Efekty uboczne będzie wykonywany w kolejności. Proces następnie rozpoczyna się ponownie z obliczania *wyrażenia warunkowego*.  
  
    -   Jeśli *wyrażenia warunkowego* zostanie pominięty, *wyrażenia warunkowego* jest traktowane jako wartość true i wykonania procesu dokładnie, jak opisano w poprzednim akapicie. A **dla** instrukcję bez *wyrażenia warunkowego* argument kończy tylko wtedy, gdy **podziału** lub **zwracać** instrukcji w instrukcji treść jest wykonywane, lub gdy **goto** (etykietą instrukcji poza **dla** treść instrukcji) jest wykonywana.  
  
    -   Jeśli *wyrażenia warunkowego* jest **false** (0), wykonywanie **dla** kończy instrukcji i kontrola przechodzi do następnej instrukcji w programie.  
  
 A **dla** instrukcji także kiedy kończy **podziału**, **goto**, lub **zwracać** wykonaniu instrukcji w treści instrukcji. A **kontynuować** instrukcji w **dla** powoduje, że w pętli *pętli wyrażenie* ma zostać obliczone. Gdy **podziału** instrukcja jest wykonywana wewnątrz **dla** pętli, *pętli wyrażenie* nie jest obliczane lub wykonać. Ta instrukcja  
  
```  
for( ;; )  
```  
  
 zwyczajowe sposób utworzyć nieskończoną pętlę, który tylko może być zakończony z **podziału**, **goto**, lub **zwracać** instrukcji.  
  
## <a name="code"></a>Kod  
 W tym przykładzie przedstawiono **dla** instrukcji:  
  
```  
// c_for.c  
int main()  
{  
   char* line = "H e  \tl\tlo World\0";  
   int space = 0;  
   int tab = 0;  
   int i;  
   int max = strlen(line);  
   for (i = 0; i < max; i++ )   
   {  
      if ( line[i] == ' ' )  
      {  
          space++;  
      }  
      if ( line[i] == '\t' )  
      {  
          tab++;  
      }  
   }  
  
   printf("Number of spaces: %i\n", space);  
   printf("Number of tabs: %i\n", tab);  
   return 0;  
}  
```  
  
## <a name="output"></a>Dane wyjściowe  
  
```  
Number of spaces: 4  
Number of tabs: 2  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje](../c-language/statements-c.md)