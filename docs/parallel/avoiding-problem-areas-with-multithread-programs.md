---
title: Unikanie obszarów problemów z programami wielowątkowymi | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- multithreading [C++], troubleshooting
- errors [C++], multithreaded programs
- threading [C++], troubleshooting
- troubleshooting [C++], multithreading
ms.assetid: 06cc231d-bb5a-409d-8bd3-676c9e2a8c5b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5af4c1ca6a86b2cff457aee12e8337103ce7f42d
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33686617"
---
# <a name="avoiding-problem-areas-with-multithread-programs"></a>Unikanie obszarów problemów z programami wielowątkowymi
Istnieje kilka problemów, które mogą wystąpić w tworzeniu, łączenie i wykonywania program więlowątkowy w języku C. W poniższej tabeli opisano niektóre z najczęściej problemów. (Omówienie podobne z punktu widzenia MFC, zobacz [Multithreading: Programowanie porady](../parallel/multithreading-programming-tips.md).)  
  
|Problem|Prawdopodobna przyczyna|  
|-------------|--------------------|  
|Otrzymasz komunikat, pokazujący, że program spowodował naruszenie ochrony.|Wiele błędów programowania Win32 spowodować naruszeń ochrony. Typową przyczyną naruszeń ochrony jest przypisanie pośrednich danych do wskaźników o wartości null. Ponieważ powoduje to program próby uzyskania dostępu do pamięci, który nie należy do niego, zgłaszany jest naruszenie ochrony.<br /><br /> Łatwo wykryć przyczynę naruszenie ochrony jest kompilacji programu z informacji o debugowaniu, a następnie uruchom go za pomocą debugera w środowisku Visual C++. W przypadku wystąpienia błędu ochrony systemu Windows przeniesie formantu do debugera i kursor znajduje się w wierszu, który spowodował problem.|  
|Program generuje wiele błędów kompilacji i łącza.|Wiele potencjalnych problemów można wyeliminować, ustawiając poziom ostrzeżeń kompilatora do jednego z jego największe wartości i heeding komunikaty ostrzegawcze. Przy użyciu poziomu 3 lub poziom 4 ostrzeżenia poziomu opcje, można wykryć konwersji danych przypadkowe, brak prototypy funkcji i korzystanie z funkcji standardem ANSI.|  
  
## <a name="see-also"></a>Zobacz też  
 [Wielowątkowość z językiem C i podsystemem Win32](../parallel/multithreading-with-c-and-win32.md)