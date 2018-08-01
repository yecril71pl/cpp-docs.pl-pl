---
title: 'Porady: Tworzenie wystąpień weak_ptr i korzystanie | Dokumentacja firmy Microsoft'
ms.custom: how-to
ms.date: 07/12/2018
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
ms.openlocfilehash: 673bceb5042a91361ece00360c4d9c5b140e4d00
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2018
ms.locfileid: "39402702"
---
# <a name="how-to-create-and-use-weakptr-instances"></a>Porady: tworzenie wystąpień weak_ptr i korzystanie z nich
Czasami obiekt musi przechowywać sposób dostępu do podstawowego obiektu z obiektu `shared_ptr` bez zwiększania licznika odwołań rośnie. Zazwyczaj ta sytuacja występuje kiedy istnieją cykliczne odwołania między `shared_ptr` wystąpień.  

 Projekt najlepiej jest unikać wspólnej własności wskaźników, kiedy to tylko możliwe. Jednakże jeśli musisz współużytkować własność `shared_ptr` wystąpień, unikaj odwołań cyklicznych między nimi. Gdy odwołania cykliczne są nieuniknione lub preferowane jakiegoś powodu, użyj `weak_ptr` zapewnienie jednego lub większej ilości właścicieli słabe odwołanie do innego `shared_ptr`. Za pomocą `weak_ptr`, możesz utworzyć `shared_ptr` dołącza do istniejącego zestawu wystąpień powiązanych, ale tylko wtedy, jeśli zasób pamięci podstawowej jest nadal ważny. A `weak_ptr` sam nie uczestniczy w zliczaniu odwołań i dlatego jego nie uniemożliwia licznik odwołań odwołańdo zera. Można jednak użyć `weak_ptr` by spróbować uzyskać nową kopię `shared_ptr` za pomocą którego został zainicjowany. Jeśli pamięć już została usunięta, `bad_weak_ptr` wyjątku. Jeśli pamięć jest nadal ważny, nowy wspólny wskaźnik zwiększa liczbę odwołań i gwarantuje, że pamięć będzie obowiązywać tak długo, jak `shared_ptr` zmiennej pozostaje w zakresie.  

## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje przypadek gdzie `weak_ptr` służy do zapewnienia prawidłowego usuwania obiektów, które mają zależności cykliczne. Jak analizując przykład założono, że został on utworzony tylko wtedy, gdy zostały rozważone alternatywne rozwiązania. `Controller` Obiekty reprezentują niektóre aspekty procesu maszynowego i działają one niezależnie. Każdy kontroler musi być w stanie zbadać stan innych kontrolerów w dowolnym momencie, a każdy z nich zawiera prywatny `vector<weak_ptr<Controller>>` do tego celu. Każdy wektor zawiera odwołanie cykliczne, dlatego `weak_ptr` wystąpienia są używane zamiast `shared_ptr`.  

 [!code-cpp[stl_smart_pointers#222](../cpp/codesnippet/CPP/how-to-create-and-use-weak-ptr-instances_1.cpp)]  

```Output  
Creating Controller0  
Creating Controller1  
Creating Controller2  
Creating Controller3  
Creating Controller4  
push_back to v[0]: 1  
push_back to v[0]: 2  
push_back to v[0]: 3  
push_back to v[0]: 4  
push_back to v[1]: 0  
push_back to v[1]: 2  
push_back to v[1]: 3  
push_back to v[1]: 4  
push_back to v[2]: 0  
push_back to v[2]: 1  
push_back to v[2]: 3  
push_back to v[2]: 4  
push_back to v[3]: 0  
push_back to v[3]: 1  
push_back to v[3]: 2  
push_back to v[3]: 4  
push_back to v[4]: 0  
push_back to v[4]: 1  
push_back to v[4]: 2  
push_back to v[4]: 3
use_count = 1  
Status of 1 = On  
Status of 2 = On  
Status of 3 = On  
Status of 4 = On  
use_count = 1  
Status of 0 = On  
Status of 2 = On  
Status of 3 = On  
Status of 4 = On  
use_count = 1  
Status of 0 = On  
Status of 1 = On  
Status of 3 = On  
Status of 4 = On  
use_count = 1  
Status of 0 = O  
nStatus of 1 = On  
Status of 2 = On  
Status of 4 = On  
use_count = 1  
Status of 0 = On  
Status of 1 = On  
Status of 2 = On  
Status of 3 = On  
Destroying Controller0  
Destroying Controller1  
Destroying Controller2  
Destroying Controller3  
Destroying Controller4  
Press any key  
```  

 Jako eksperyment, należy zmodyfikować wektor `others` jako `vector<shared_ptr<Controller>>`, a następnie w danych wyjściowych, zwróć uwagę, że destruktory nie są wywoływane gdy `TestRun` zwraca.  

## <a name="see-also"></a>Zobacz także  
 [Wskaźniki inteligentne](../cpp/smart-pointers-modern-cpp.md)