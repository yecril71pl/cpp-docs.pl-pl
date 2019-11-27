---
title: 'Instrukcje: Tworzenie wystąpień weak_ptr i korzystanie z nich'
ms.custom: how-to
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: 8dd6909b-b070-4afa-9696-f2fc94579c65
ms.openlocfilehash: 32e8d64fdb6449f1d40aec4161bfda54987ca66a
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2019
ms.locfileid: "74245606"
---
# <a name="how-to-create-and-use-weak_ptr-instances"></a>Instrukcje: Tworzenie wystąpień weak_ptr i korzystanie z nich

Czasami obiekt musi przechowywać sposób dostępu do obiektu bazowego [shared_ptr](../standard-library/shared-ptr-class.md) bez powodowania zwiększenia liczby odwołań. Zazwyczaj ta sytuacja występuje, gdy istnieją cykliczne odwołania między wystąpieniami `shared_ptr`.

Najlepszym rozwiązaniem jest uniknięcie wspólnej własności wskaźników w każdym momencie. Jeśli jednak użytkownik musi mieć współużytkowaną własność wystąpień `shared_ptr`, należy unikać cyklicznych odwołań między nimi. Gdy odwołania cykliczne są niemożliwe do uniknięcia lub nawet z jakiegoś powodu, należy użyć [weak_ptr](../standard-library/weak-ptr-class.md) , aby nadać jednemu lub większej liczbie właścicieli słabe odwołanie do innego `shared_ptr`. Za pomocą `weak_ptr`można utworzyć `shared_ptr`, który łączy się z istniejącym zestawem powiązanych wystąpień, ale tylko wtedy, gdy zasób pamięci źródłowej jest nadal ważny. `weak_ptr` samo nie uczestniczy w zliczaniu odwołań, dlatego nie może zapobiec występowaniu liczby odwołań z przechodzenia do zera. Można jednak użyć `weak_ptr`, aby próbować uzyskać nową kopię `shared_ptr`, z którą została zainicjowana. Jeśli pamięć została już usunięta, operator bool `weak_ptr`zwraca `false`. Jeśli pamięć jest nadal ważna, nowy udostępniony wskaźnik zwiększa liczbę odwołań i gwarantuje, że pamięć będzie obowiązywać, o ile zmienna `shared_ptr` pozostaje w zakresie.

## <a name="example"></a>Przykład

Poniższy przykład kodu pokazuje przypadek, gdzie `weak_ptr` jest używany do zapewnienia prawidłowego usuwania obiektów, które mają zależności cykliczne. Podczas badania przykładu Załóżmy, że został on utworzony dopiero po rozważenia rozwiązań alternatywnych. Obiekty `Controller` reprezentują kilka aspektów procesu maszynowego i działają niezależnie. Każdy kontroler musi mieć możliwość zbadania stanu innych kontrolerów w dowolnym momencie, a każdy z nich zawiera `vector<weak_ptr<Controller>>` prywatny do tego celu. Każdy wektor zawiera odwołanie cykliczne i w związku z tym są używane `weak_ptr` wystąpienia, a nie `shared_ptr`.

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

W ramach eksperymentu zmodyfikuj `others` wektora jako `vector<shared_ptr<Controller>>`, a następnie w danych wyjściowych Zwróć uwagę, że żadne destruktory nie są wywoływane, gdy `TestRun` zwraca.

## <a name="see-also"></a>Zobacz także

[Wskaźniki inteligentne (Modern C++)](../cpp/smart-pointers-modern-cpp.md)
