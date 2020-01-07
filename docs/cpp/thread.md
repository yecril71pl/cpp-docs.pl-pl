---
title: wątek
ms.date: 05/07/2019
f1_keywords:
- thread_cpp
helpviewer_keywords:
- thread local storage (TLS)
- thread __declspec keyword
- TLS (thread local storage), compiler implementation
- __declspec keyword [C++], thread
ms.assetid: 667f2a77-6d1f-4b41-bee8-05e67324fab8
ms.openlocfilehash: cc21602764a9a3c2584bdd7da62c75974ffdd5fb
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301291"
---
# <a name="thread"></a>wątek

**Microsoft Specific**

Rozszerzony modyfikator klasy magazynu **wątku** jest używany do deklarowania zmiennej lokalnej wątku. Dla przenośnego odpowiednika w języku C++ 11 i nowszych Użyj specyfikatora klasy magazynu [thread_local](../cpp/storage-classes-cpp.md#thread_local) dla kodu przenośnego. W systemie Windows **thread_local** jest zaimplementowany przy użyciu **__declspec (thread)** .

## <a name="syntax"></a>Składnia

**__declspec (wątek)** *deklarator*

## <a name="remarks"></a>Uwagi

Pamięć lokalna wątku (TLS) to mechanizm, za pomocą którego każdy wątek w procesie wielowątkowym przydziela pamięć dla danych specyficznych wątku. W standardowych programach wielowątkowych, dane są współużytkowane przez wszystkie wątki danego procesu, natomiast pamięć lokalna wątku jest mechanizmem przydzielania danych osobno dla danego wątku. Aby uzyskać pełną dyskusję na temat wątków, zobacz [wielowątkowość](../parallel/multithreading-support-for-older-code-visual-cpp.md).

Deklaracje zmiennych lokalnych wątku muszą używać [składni atrybutów rozszerzonych](../cpp/declspec.md) i słowa kluczowego **__declspec** ze słowem kluczowym **wątku** . Na przykład, poniższy kod deklaruje lokalną zmienną całkowitą wątku i inicjuje ją wartością:

```cpp
__declspec( thread ) int tls_i = 1;
```

W przypadku używania zmiennych lokalnych wątków w dynamicznie ładowanych bibliotekach należy wiedzieć o czynnikach, które mogą spowodować, że zmienna lokalna wątku nie zostanie poprawnie zainicjowana:

1. Jeśli zmienna jest inicjowana za pomocą wywołania funkcji (w tym konstruktorów), ta funkcja będzie wywoływana tylko dla wątku, który spowodował załadowanie pliku binarnego/DLL do procesu i dla tych wątków, które rozpoczęły się po załadowaniu pliku binarnego/DLL. Funkcje inicjujące nie są wywoływane dla żadnego innego wątku, który został już uruchomiony podczas ładowania biblioteki DLL. Dynamiczna Inicjalizacja występuje w wywołaniu DllMain dla DLL_THREAD_ATTACH, ale biblioteka DLL nigdy nie pobiera tego komunikatu, jeśli biblioteka DLL nie jest w toku podczas uruchamiania wątku.

1. Zmienne lokalne wątku, które są inicjowane statycznie z wartościami stałymi, są zwykle inicjowane prawidłowo we wszystkich wątkach. Jednakże od grudnia 2017 istnieje znany problem związany z zgodnością w kompilatorze firmy Microsoft C++ , w którym zmienne **constexpr** są odbierane jako dynamiczne, a nie statyczne.

   Uwaga: oczekiwano, że oba te problemy zostaną rozwiązane w przyszłych aktualizacjach kompilatora.

Ponadto należy przestrzegać następujących wytycznych podczas deklarowania lokalnych obiektów wątku i zmiennych:

- Atrybut **Thread** można zastosować tylko do deklaracji klasy i danych oraz definicji; nie można użyć **wątku** dla deklaracji lub definicji funkcji.

- Można określić atrybut **wątku** tylko dla elementów danych ze statycznym okresem przechowywania. Obejmuje to globalne obiekty danych (zarówno **statyczne** , jak i zewnętrzne), lokalne obiekty **statyczne i statyczne**elementy członkowskie danych klas. Nie można zadeklarować automatycznych obiektów danych przy użyciu atrybutu **wątku** .

- Należy użyć atrybutu **wątku** dla deklaracji i definicji obiektu lokalnego wątku, niezależnie od tego, czy deklaracja i definicja występują w tym samym pliku lub oddzielnych plikach.

- Nie można użyć atrybutu **wątku** jako modyfikatora typu.

- Ponieważ deklaracja obiektów, które używają atrybutu **wątku** , jest dozwolona, te dwa przykłady są semantycznie równoważne:

    ```cpp
    // declspec_thread_2.cpp
    // compile with: /LD
    __declspec( thread ) class B {
    public:
       int data;
    } BObject;   // BObject declared thread local.

    class B2 {
    public:
       int data;
    };
    __declspec( thread ) B2 BObject2;   // BObject2 declared thread local.
    ```

- Standard C pozwala na inicjalizację obiektu lub zmiennej z wyrażeniem, w którym uczestniczy odwołanie do samego siebie, ale tylko dla obiektów niestatycznych. Mimo C++ że zwykle zezwala na to dynamiczną inicjalizację obiektu z wyrażeniem, w którym jest odwołanie do samego siebie, ten typ inicjalizacji nie jest dozwolony w przypadku obiektów lokalnych wątków. Na przykład:

   ```cpp
   // declspec_thread_3.cpp
   // compile with: /LD
   #define Thread __declspec( thread )
   int j = j;   // Okay in C++; C error
   Thread int tls_i = sizeof( tls_i );   // Okay in C and C++
   ```

   Wyrażenie **sizeof** , które obejmuje inicjowany obiekt, nie stanowi odwołania do samego siebie i jest dozwolone w C i C++.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[__declspec](../cpp/declspec.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[Lokalny magazyn wątków (TLS)](../parallel/thread-local-storage-tls.md)