---
title: "Unikanie obszarów problemów z programami wielowątkowymi | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- multithreading [C++], troubleshooting
- errors [C++], multithreaded programs
- threading [C++], troubleshooting
- troubleshooting [C++], multithreading
ms.assetid: 06cc231d-bb5a-409d-8bd3-676c9e2a8c5b
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 546f5b5daa88578fc7dd062018257f0929bc0cff
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="avoiding-problem-areas-with-multithread-programs"></a>Unikanie obszarów problemów z programami wielowątkowymi
Istnieje kilka problemów, które mogą wystąpić w tworzeniu, łączenie i wykonywania program więlowątkowy w języku C. W poniższej tabeli opisano niektóre z najczęściej problemów. (Omówienie podobne z punktu widzenia MFC, zobacz [Multithreading: Programowanie porady](../parallel/multithreading-programming-tips.md).)  
  
|Problem|Prawdopodobna przyczyna|  
|-------------|--------------------|  
|Otrzymasz komunikat, pokazujący, że program spowodował naruszenie ochrony.|Wiele błędów programowania Win32 spowodować naruszeń ochrony. Typową przyczyną naruszeń ochrony jest przypisanie pośrednich danych do wskaźników o wartości null. Ponieważ powoduje to program próby uzyskania dostępu do pamięci, który nie należy do niego, zgłaszany jest naruszenie ochrony.<br /><br /> Łatwo wykryć przyczynę naruszenie ochrony jest kompilacji programu z informacji o debugowaniu, a następnie uruchom go za pomocą debugera w środowisku Visual C++. W przypadku wystąpienia błędu ochrony systemu Windows przeniesie formantu do debugera i kursor znajduje się w wierszu, który spowodował problem.|  
|Program generuje wiele błędów kompilacji i łącza.|Wiele potencjalnych problemów można wyeliminować, ustawiając poziom ostrzeżeń kompilatora do jednego z jego największe wartości i heeding komunikaty ostrzegawcze. Przy użyciu poziomu 3 lub poziom 4 ostrzeżenia poziomu opcje, można wykryć konwersji danych przypadkowe, brak prototypy funkcji i korzystanie z funkcji standardem ANSI.|  
  
## <a name="see-also"></a>Zobacz też  
 [Wielowątkowość z językiem C i podsystemem Win32](../parallel/multithreading-with-c-and-win32.md)