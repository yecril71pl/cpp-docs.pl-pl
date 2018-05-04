---
title: 'Porady: Tworzenie wystąpień weak_ptr i korzystanie | Dokumentacja firmy Microsoft'
ms.custom: how-to
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 8dd6909b-b070-4afa-9696-f2fc94579c65
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a8fbbf9d3b427c2451fafe0fae93a531dfd45ad8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-create-and-use-weakptr-instances"></a>Porady: tworzenie wystąpień weak_ptr i korzystanie z nich
Czasami muszą być przechowywane sposobem uzyskania dostępu do obiektu źródłowego obiektu `shared_ptr` bez spowodowania, że liczba odwołań do jest zwiększany. Zwykle ta sytuacja występuje, gdy masz cykliczne odwołanie pomiędzy `shared_ptr` wystąpień.  
  
 Projekt najlepiej jest uniknąć udostępnionego własność wskaźników zawsze, gdy użytkownik może. Jednak jeśli należy udostępnić własność `shared_ptr` wystąpienia, należy unikać odwołania cykliczne między nimi. Gdy odwołania cykliczne są nieuniknione lub nawet preferowanym jakiegoś powodu, użyj `weak_ptr` aby zapewnić co najmniej jeden właścicieli słabe odwołanie do innego `shared_ptr`. Za pomocą `weak_ptr`, można utworzyć `shared_ptr` dołączaną do istniejącego zestawu powiązanych wystąpień, ale tylko wtedy, jeśli podstawowy zasobów pamięci jest nadal ważny. A `weak_ptr` sam nie uczestniczy w liczenie odwołań i w związku z tym go nie można zapobiec liczba odwołań do zera. Można jednak użyć `weak_ptr` spróbować uzyskać nową kopię `shared_ptr` z którego został zainicjowany. Jeśli została już usunięta pamięć, **bad_weak_ptr —** wyjątku. Jeśli ilość pamięci jest nadal ważny, nowy wskaźnik udostępnionego zwiększa liczbę odwołania i gwarantuje, że pamięć będzie nieprawidłowa tak długo, jak `shared_ptr` zmiennej pozostaje w zakresie.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje przypadku gdzie `weak_ptr` służy do zapewnienia prawidłowego usuwania obiektów, które mają zależności cykliczne. Jako przykład należy zbadać, założono, że została ona utworzona tylko wtedy, gdy zostały uznane za rozwiązań alternatywnych. `Controller` Reprezentować niektórych aspektów procesu maszyny i działają niezależnie. Każdy kontroler musi być w stanie zapytać o stan innych kontrolerów w dowolnym momencie, a każda z nich zawiera prywatnej `vector<weak_ptr<Controller>>` w tym celu. Każdy wektor zawiera odwołanie cykliczne i w związku z tym `weak_ptr` wystąpienia są używane zamiast `shared_ptr`.  
  
 [!code-cpp[stl_smart_pointers#222](../cpp/codesnippet/CPP/how-to-create-and-use-weak-ptr-instances_1.cpp)]  
  
```Output  
Creating Controller0Creating Controller1Creating Controller2Creating Controller3Creating Controller4push_back to v[0]: 1push_back to v[0]: 2push_back to v[0]: 3push_back to v[0]: 4push_back to v[1]: 0push_back to v[1]: 2push_back to v[1]: 3push_back to v[1]: 4push_back to v[2]: 0push_back to v[2]: 1push_back to v[2]: 3push_back to v[2]: 4push_back to v[3]: 0push_back to v[3]: 1push_back to v[3]: 2push_back to v[3]: 4push_back to v[4]: 0push_back to v[4]: 1push_back to v[4]: 2push_back to v[4]: 3use_count = 1Status of 1 = OnStatus of 2 = OnStatus of 3 = OnStatus of 4 = Onuse_count = 1Status of 0 = OnStatus of 2 = OnStatus of 3 = OnStatus of 4 = Onuse_count = 1Status of 0 = OnStatus of 1 = OnStatus of 3 = OnStatus of 4 = Onuse_count = 1Status of 0 = OnStatus of 1 = OnStatus of 2 = OnStatus of 4 = Onuse_count = 1Status of 0 = OnStatus of 1 = OnStatus of 2 = OnStatus of 3 = OnDestroying Controller0Destroying Controller1Destroying Controller2Destroying Controller3Destroying Controller4Press any key  
```  
  
 Jako eksperyment, zmodyfikuj wektor `others` jako `vector<shared_ptr<Controller>>`i w danych wyjściowych, zwróć uwagę, że destruktory nie są wywoływane podczas `TestRun` zwraca.  
  
## <a name="see-also"></a>Zobacz też  
 [Wskaźniki inteligentne](../cpp/smart-pointers-modern-cpp.md)