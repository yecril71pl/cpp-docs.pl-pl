---
title: 'Porady: Określanie specjalnych zasad harmonogramu | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- specifying scheduler policies [Concurrency Runtime]
- scheduler policies, specifying [Concurrency Runtime]
ms.assetid: 9c5149f9-ac34-4ff3-9e79-0bad103e4e6b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 578743fc9ffc6931e596a1b924282544f5ee9601
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46435418"
---
# <a name="how-to-specify-specific-scheduler-policies"></a>Porady: określanie specjalnych zasad harmonogramu

Zasady harmonogramu pozwalają na kontrolę strategii, używany w harmonogramie podczas zarządzania zadaniami. W tym temacie pokazano, jak używać zasadę harmonogramu umożliwia podwyższenie priorytetu wątku zadania, które wyświetla wskaźnik postępu do konsoli.

Na przykład, który używa zasad harmonogramu niestandardowego wraz z agentów asynchronicznych, zobacz [porady: tworzenie agentów tego zasad użycia określonego harmonogramu](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md).

## <a name="example"></a>Przykład

Poniższy przykład wykonuje dwa zadania. Pierwsze zadanie oblicza n<sup>th</sup> Fibonacci numer. Drugie zadanie wyświetla wskaźnik postępu do konsoli.

Pierwsze zadanie używa dekompozycji cykliczne do obliczenia liczby Fibonacci. Oznacza to każdy rekursywnie zadanie tworzy podzadania do obliczenia ogólny wynik. Zadanie, które używa dekompozycji cyklicznego mogą używać wszystkich dostępnych zasobów, a tym samym blokować innych zadań. W tym przykładzie zadanie, które wyświetla wskaźnik postępu może nie odbierać szybki dostęp do zasobów obliczeniowych.

Aby zapewnić zadanie, które wyświetla postęp komunikat uczciwego dostępu do zasobów obliczeniowych, w tym przykładzie użyto kroki, które są opisane w [porady: Zarządzanie wystąpieniem harmonogramu](../../parallel/concrt/how-to-manage-a-scheduler-instance.md) można utworzyć wystąpienia harmonogramu, zawierającej zasady niestandardowe. Zasady niestandardowe określa priorytet wątku za najwyższy priorytet.

W tym przykładzie użyto [concurrency::call](../../parallel/concrt/reference/call-class.md) i [concurrency::timer](../../parallel/concrt/reference/timer-class.md) klasy, aby wydrukować wskaźnik postępu. Te klasy mają wersji ich konstruktory, które przyjmują odwołania do [concurrency::Scheduler](../../parallel/concrt/reference/scheduler-class.md) obiektu, która planuje je. W przykładzie użyto domyślnego harmonogramu, aby zaplanować zadanie, które oblicza liczbę Fibonacci i wystąpieniem harmonogramu, aby zaplanować zadanie, które wyświetla wskaźnik postępu.

Aby zilustrować korzyści z używania harmonogram, który ma zasady niestandardowe, w tym przykładzie wykonuje całego zadania dwa razy. W przykładzie najpierw użyto domyślnego harmonogramu można zaplanować zarówno do zadań. Następnie w przykładzie wykorzystano domyślnego harmonogramu, aby zaplanować uruchamianie pierwszego zadania i harmonogram, który ma zasady niestandardowe, aby zaplanować drugie zadanie podrzędne.

[!code-cpp[concrt-scheduler-policy#1](../../parallel/concrt/codesnippet/cpp/how-to-specify-specific-scheduler-policies_1.cpp)]

Ten przykład generuje następujące dane wyjściowe.

```Output
Default scheduler:
...........................................................................done
Scheduler that has a custom policy:
...........................................................................done
```

Mimo że oba zestawy zadań daje ten sam wynik, wersji, która używa niestandardowych zasad włącza zadanie, które wyświetla wskaźnik postępu uruchomienie priorytetem z podwyższonym poziomem uprawnień, tak, aby zachowuje się bardziej elastycznie zmieniać.

## <a name="compiling-the-code"></a>Kompilowanie kodu

Kopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `scheduler-policy.cpp` , a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

**Usługa scheduler-policy.cpp dla cl.exe/ehsc**

## <a name="see-also"></a>Zobacz też

[Zasady harmonogramu](../../parallel/concrt/scheduler-policies.md)<br/>
[Instrukcje: zarządzanie wystąpieniem harmonogramu](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)<br/>
[Instrukcje: tworzenie agentów korzystających ze specjalnych zasad harmonogramu](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md)

