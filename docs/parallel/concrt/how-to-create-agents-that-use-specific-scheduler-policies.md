---
title: 'Porady: tworzenie agentów korzystających ze specjalnych zasad harmonogramu'
ms.date: 11/04/2016
helpviewer_keywords:
- scheduler policies, agents [Concurrency Runtime]
- creating agents that use specific policies [Concurrency Runtime]
ms.assetid: 46a3e265-0777-4ec3-a142-967bafc49d67
ms.openlocfilehash: ece6b113e3fe10c2c3179517f73137df281acf87
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141737"
---
# <a name="how-to-create-agents-that-use-specific-scheduler-policies"></a>Porady: tworzenie agentów korzystających ze specjalnych zasad harmonogramu

Agent to składnik aplikacji, który działa asynchronicznie z innymi składnikami w celu rozwiązywania większych zadań obliczeniowych. Agent ma zwykle ustawiony cykl życia i utrzymuje stan.

Każdy agent może mieć unikatowe wymagania dotyczące aplikacji. Na przykład Agent, który umożliwia interakcję użytkownika (pobranie danych wejściowych lub wyświetlanie danych wyjściowych) może wymagać wyższego priorytetu dostępu do zasobów obliczeniowych. Zasady usługi Scheduler umożliwiają sterowanie strategią używaną przez harmonogram podczas zarządzania zadaniami. W tym temacie przedstawiono sposób tworzenia agentów korzystających z określonych zasad usługi Scheduler.

Aby zapoznać się z podstawowym przykładem używającym niestandardowych zasad usługi Scheduler wraz z blokami komunikatów asynchronicznych, zobacz [How to: Określanie określonych zasad usługi Scheduler](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md).

W tym temacie są stosowane funkcje z biblioteki agentów asynchronicznych, takich jak agenci, bloki komunikatów i funkcje przekazywania komunikatów, aby wykonać prace. Aby uzyskać więcej informacji na temat biblioteki agentów asynchronicznych, zobacz [Biblioteka agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md).

## <a name="example"></a>Przykład

Poniższy przykład definiuje dwie klasy, które pochodzą od [concurrency:: Agent](../../parallel/concrt/reference/agent-class.md): `permutor` i `printer`. Klasa `permutor` oblicza wszystkie permutacje danego ciągu wejściowego. Klasa `printer` drukuje komunikaty o postępie w konsoli programu. Klasa `permutor` wykonuje operację obliczeniową intensywnie, która może korzystać ze wszystkich dostępnych zasobów obliczeniowych. Aby było to przydatne, Klasa `printer` musi drukować każdy komunikat o postępie w odpowiednim czasie.

Aby zapewnić, że Klasa `printer` uzyskać dostęp do zasobów obliczeniowych, w tym przykładzie są używane kroki opisane w artykule [How to: Manage a Scheduler instance](../../parallel/concrt/how-to-manage-a-scheduler-instance.md) to Create a Scheduler Policy, który ma zasady niestandardowe. Zasady niestandardowe określają priorytet wątku, który jest klasą o najwyższym priorytecie.

Aby zilustrować zalety korzystania z harmonogramu, który ma zasady niestandardowe, ten przykład wykonuje ogólne zadanie dwa razy. W przykładzie najpierw jest planowane zaplanowanie obu zadań przy użyciu domyślnego harmonogramu. Ten przykład używa domyślnego harmonogramu do zaplanowania obiektu `permutor` oraz harmonogramu, który ma zasady niestandardowe do zaplanowania obiektu `printer`.

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

Mimo że oba zestawy zadań tworzą ten sam wynik, wersja, która korzysta z zasad niestandardowych, umożliwia uruchamianie `printer` obiektu z podwyższonym priorytetem, dzięki czemu będzie bardziej reagować.

## <a name="compiling-the-code"></a>Kompilowanie kodu

Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `permute-strings.cpp` a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

> **CL. exe/EHsc Permute-Strings. cpp**

## <a name="see-also"></a>Zobacz też

[Zasady harmonogramu](../../parallel/concrt/scheduler-policies.md)<br/>
[Agenci asynchroniczni](../../parallel/concrt/asynchronous-agents.md)
