---
title: 'Instrukcje: Tworzenie wystąpień weak_ptr i korzystanie z nich'
ms.custom: how-to
ms.date: 09/18/2019
ms.topic: conceptual
ms.assetid: 8dd6909b-b070-4afa-9696-f2fc94579c65
ms.openlocfilehash: e5d1b13d894a617ca514e26f14fde3f514540d34
ms.sourcegitcommit: 76cc69b482ada8ebf0837e8cdfd4459661f996dd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71127183"
---
# <a name="how-to-create-and-use-weak_ptr-instances"></a>Instrukcje: Tworzenie wystąpień weak_ptr i korzystanie z nich

Czasami obiekt musi przechowywać sposób dostępu do obiektu bazowego a `shared_ptr` bez powodowania zwiększenia liczby odwołań. Zazwyczaj ta sytuacja występuje, gdy istnieją cykliczne odwołania między `shared_ptr` wystąpieniami.

Najlepszym rozwiązaniem jest uniknięcie wspólnej własności wskaźników w każdym momencie. Jeśli jednak użytkownik musi mieć współużytkowaną własność `shared_ptr` wystąpień, należy unikać cyklicznych odwołań między nimi. Gdy odwołania cykliczne są niemożliwe do uniknięcia lub nawet preferowane z jakiegoś powodu, `weak_ptr` należy użyć, aby nadać jednemu lub większej liczbie właścicieli słabe `shared_ptr`odwołanie do innego. Za pomocą `weak_ptr`, można `shared_ptr` utworzyć sprzężenie do istniejącego zestawu powiązanych wystąpień, ale tylko wtedy, gdy zasób pamięci bazowej jest nadal ważny. `weak_ptr` Samo nie uczestniczy w zliczaniu odwołań i w związku z tym nie może zapobiec występowaniu liczby odwołań z przechodzenia do zera. Można jednak użyć elementu `weak_ptr` , aby spróbować uzyskać nową kopię, `shared_ptr` z którą została zainicjowana. Jeśli pamięć została już usunięta, `weak_ptr`operator logiczny zwraca wartość. `false` Jeśli pamięć jest nadal ważna, nowy udostępniony wskaźnik zwiększa liczbę odwołań i gwarantuje, że pamięć będzie obowiązywać `shared_ptr` , o ile zmienna pozostaje w zakresie.

## <a name="example"></a>Przykład

Poniższy przykład kodu pokazuje przypadek, gdzie `weak_ptr` służy do zapewnienia prawidłowego usuwania obiektów, które mają zależności cykliczne. Podczas badania przykładu Załóżmy, że został on utworzony dopiero po rozważenia rozwiązań alternatywnych. `Controller` Obiekty reprezentują jakiś aspekt procesu maszynowego i działają niezależnie. Każdy kontroler musi mieć możliwość zbadania stanu innych kontrolerów w dowolnym momencie, a każdy z nich zawiera prywatne `vector<weak_ptr<Controller>>` do tego celu. Każdy wektor zawiera odwołanie cykliczne i w `weak_ptr` związku z `shared_ptr`tym są używane wystąpienia zamiast.

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
Status of 0 = On
Status of 1 = On
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

W ramach eksperymentu zmodyfikuj wektor `others` `vector<shared_ptr<Controller>>`jako, a następnie w danych wyjściowych Zwróć uwagę, że żadne destruktory nie są wywoływane po `TestRun` powrocie.

## <a name="see-also"></a>Zobacz także

[Wskaźniki inteligentne (Modern C++)](../cpp/smart-pointers-modern-cpp.md)
