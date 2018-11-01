---
title: Unikanie obszarów problemów z programami wielowątkowymi
ms.date: 11/04/2016
helpviewer_keywords:
- multithreading [C++], troubleshooting
- errors [C++], multithreaded programs
- threading [C++], troubleshooting
- troubleshooting [C++], multithreading
ms.assetid: 06cc231d-bb5a-409d-8bd3-676c9e2a8c5b
ms.openlocfilehash: 598758a4ceb0a12640faf2832f9f03cd1e44ef9f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50461649"
---
# <a name="avoiding-problem-areas-with-multithread-programs"></a>Unikanie obszarów problemów z programami wielowątkowymi

Jest kilka problemów, które mogą wystąpić w tworzeniu, połączeń i wykonywanie program więlowątkowy w języku C. W poniższej tabeli opisano niektóre typowe problemy. (Omówienie podobne z punktu widzenia MFC, zobacz [wielowątkowość: porady dotyczące programowania](multithreading-programming-tips.md).)

|Problem|Prawdopodobna przyczyna|
|-------------|--------------------|
|Otrzymasz komunikat, pokazujący, że program spowodował naruszenie zasad ochrony.|Wiele błędów programowania Win32 spowodować naruszenie ochrony. Częstą przyczyną naruszeń ochrony jest pośrednich przypisywania danych do wskaźników o wartości null. Ponieważ skutkiem próby uzyskania dostępu do pamięci, który nie należy do niego program zgłaszany jest naruszenie ochrony.<br /><br /> Łatwe wykrywanie przyczynę naruszenie zasad ochrony jest kompilujesz program za pomocą informacji o debugowaniu, a następnie uruchom go za pomocą debugera w środowisku Visual C++. W przypadku wystąpienia błędów ochrony Windows przekazuje sterowanie do debugera i kursor znajduje się w wierszu, który spowodował problem.|
|Program generuje wiele błędy kompilacji i link.|Przez ustawienie poziomie ostrzeżenia kompilatora do jednej z jej największe wartości i heeding komunikaty ostrzegawcze, można wyeliminować wiele potencjalnych problemów. Przy użyciu poziomu 3 lub opcje poziomu ostrzeżenia poziomu 4, można wykryć konwersje danych niezamierzone, brak prototypy funkcji i korzystania z funkcji ze standardem ANSI.|

## <a name="see-also"></a>Zobacz też

[Wielowątkowość z językiem C i podsystemem Win32](multithreading-with-c-and-win32.md)