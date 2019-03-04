---
title: 'Instrukcje: Tworzenie agentów korzystających ze specjalnych zasad harmonogramu'
ms.date: 11/04/2016
helpviewer_keywords:
- scheduler policies, agents [Concurrency Runtime]
- creating agents that use specific policies [Concurrency Runtime]
ms.assetid: 46a3e265-0777-4ec3-a142-967bafc49d67
ms.openlocfilehash: 5aac86801015549b5552b51c06a30f8398346a06
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57257374"
---
# <a name="how-to-create-agents-that-use-specific-scheduler-policies"></a>Instrukcje: Tworzenie agentów korzystających ze specjalnych zasad harmonogramu

Agent jest składnik aplikacji asynchronicznie współpracuje z innymi składnikami rozwiązania bardziej złożone zadania obliczeniowe. Agent zazwyczaj ma ustawiony cykl życia i zachowuje stan.

Każdy agent może mieć wymagań aplikacji. Na przykład agent, który umożliwia interakcji z użytkownikiem (Pobieranie danych wejściowych lub wyświetlanie danych wyjściowych) mogą wymagać wyższej priorytetowy dostęp do zasobów obliczeniowych. Zasady harmonogramu pozwalają na kontrolę strategii, używany w harmonogramie podczas zarządzania zadaniami. W tym temacie pokazano, jak tworzenie agentów korzystających ze specjalnych zasad harmonogramu.

Aby uzyskać przykład podstawowego, który używa Niestandardowy harmonogram zasad wraz z bloki komunikatów asynchronicznych, zobacz [jak: Określanie specjalnych zasad harmonogramu](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md).

Ten temat korzysta z funkcji z bibliotekę asynchronicznych agentów, np. agenci, bloki komunikatów i funkcje przekazywania komunikatów do wykonywania pracy. Aby uzyskać więcej informacji na temat bibliotekę asynchronicznych agentów, zobacz [bibliotekę asynchronicznych agentów](../../parallel/concrt/asynchronous-agents-library.md).

## <a name="example"></a>Przykład

Poniższy przykład definiuje dwie klasy, które wynikają z [concurrency::agent](../../parallel/concrt/reference/agent-class.md): `permutor` i `printer`. `permutor` Klasy oblicza wszystkie permutacji z danego ciągu wejściowego. `printer` Klasy drukuje wiadomości dotyczące postępu do konsoli. `permutor` Klasa wykonuje praktyce intensywna operacja, którego może używać wszystkich dostępnych zasobów obliczeniowych. Były przydatne, `printer` klasy należy wydrukować każdy komunikat o postępie w odpowiednim czasie.

Aby zapewnić `printer` klasy uczciwego dostępu do zasobów obliczeniowych, w tym przykładzie użyto kroki, które są opisane w [jak: Zarządzanie wystąpieniem harmonogramu](../../parallel/concrt/how-to-manage-a-scheduler-instance.md) można utworzyć wystąpienia harmonogramu, zawierającej zasady niestandardowe. Zasady niestandardowe określa priorytet wątku za najwyższy priorytet.

Aby zilustrować korzyści z używania harmonogram, który ma zasady niestandardowe, w tym przykładzie wykonuje całego zadania dwa razy. W przykładzie najpierw użyto domyślnego harmonogramu można zaplanować zarówno do zadań. Następnie w przykładzie użyto domyślnego harmonogramu można zaplanować `permutor` obiekt i harmonogram, który ma zasady niestandardowe, aby zaplanować `printer` obiektu.

[!code-cpp[concrt-permute-strings#1](../../parallel/concrt/codesnippet/cpp/how-to-create-agents-that-use-specific-scheduler-policies_1.cpp)]

Ten przykład generuje następujące dane wyjściowe.

```Output
With default scheduler:
Computing all permutations of 'Grapefruit'...
100% complete...

With higher context priority:
Computing all permutations of 'Grapefruit'...
100% complete...
```

Mimo że oba zestawy zadań daje ten sam wynik, wersji, która używa zasad niestandardowych umożliwia `printer` obiektu uruchomienie priorytetem z podwyższonym poziomem uprawnień, tak, aby zachowuje się bardziej elastycznie zmieniać.

## <a name="compiling-the-code"></a>Kompilowanie kodu

Kopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `permute-strings.cpp` , a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

**Cl.exe/ehsc permute — strings.cpp**

## <a name="see-also"></a>Zobacz także

[Zasady harmonogramu](../../parallel/concrt/scheduler-policies.md)<br/>
[Agenci asynchroniczni](../../parallel/concrt/asynchronous-agents.md)
