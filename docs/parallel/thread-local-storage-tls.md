---
title: Lokalny magazyn wątków (TLS)
ms.date: 08/09/2019
helpviewer_keywords:
- multithreading [C++], Thread Local Storage
- TLS [C++]
- threading [C++], Thread Local Storage
- storing thread-specific data
- thread attribute
- Thread Local Storage [C++]
ms.assetid: 80801907-d792-45ca-b776-df0cf2e9f197
ms.openlocfilehash: f677d7382a9747df63023bd83b104a6bb3b74c1f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222657"
---
# <a name="thread-local-storage-tls"></a>Lokalny magazyn wątków (TLS)

Lokalny magazyn wątków (TLS) to metoda, za pomocą której każdy wątek w danym procesie wielowątkowym może przydzielić lokalizacje, w których mają być przechowywane dane specyficzne dla wątku. Dynamicznie powiązane (Run-Time) dane specyficzne dla wątku są obsługiwane przez interfejs API protokołu TLS ([Funkcja TlsAlloc](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsalloc)). Win32 i kompilator języka Microsoft C++ obsługują teraz statycznie powiązane (czas ładowania) dane dla wątku oprócz istniejącej implementacji interfejsu API.

## <a name="compiler-implementation-for-tls"></a><a name="_core_compiler_implementation_for_tls"></a>Implementacja kompilatora dla protokołu TLS

**C++ 11:**  **`thread_local`** Specyfikator klasy magazynu jest zalecanym sposobem określania magazynu lokalnego wątków dla obiektów i elementów członkowskich klasy. Aby uzyskać więcej informacji, zobacz [klasy magazynu (C++)](../cpp/storage-classes-cpp.md).

MSVC udostępnia również atrybut, [wątek](../cpp/thread.md), jako modyfikator klasy rozszerzonej pamięci masowej. Użyj **`__declspec`** słowa kluczowego, aby zadeklarować **`thread`** zmienną. Na przykład, poniższy kod deklaruje lokalną zmienną całkowitą wątku i inicjuje ją wartością:

```C
__declspec( thread ) int tls_i = 1;
```

## <a name="rules-and-limitations"></a>Zasady i ograniczenia

Podczas deklarowania statycznie powiązanych obiektów i zmiennych wątków należy przestrzegać następujących wytycznych. Te wytyczne mają zastosowanie zarówno do [wątku](../cpp/thread.md) , jak i do [thread_local](../cpp/storage-classes-cpp.md):

- Ten **`thread`** atrybut może być stosowany tylko do deklaracji klasy i danych oraz definicji. Nie można jej używać w deklaracjach lub definicjach funkcji. Na przykład poniższy kod generuje błąd kompilatora:

    ```C
    __declspec( thread )void func();     // This will generate an error.
    ```

- **`thread`** Modyfikator można określić tylko dla elementów danych z **`static`** zakresem. Obejmuje to globalne obiekty danych (zarówno **`static`** i **`extern`** ), lokalne obiekty statyczne i statyczne elementy członkowskie danych klas języka C++. Nie można zadeklarować automatycznych obiektów danych przy użyciu **`thread`** atrybutu. Poniższy kod generuje błędy kompilatora:

    ```C
    void func1()
    {
        __declspec( thread )int tls_i;            // This will generate an error.
    }

    int func2(__declspec( thread )int tls_i )     // This will generate an error.
    {
        return tls_i;
    }
    ```

- Deklaracje i definicje obiektu lokalnego wątku muszą określać **`thread`** atrybut. Na przykład poniższy kod generuje błąd:

    ```C
    #define Thread  __declspec( thread )
    extern int tls_i;        // This will generate an error, since the
    int __declspec( thread )tls_i;        // declaration and definition differ.
    ```

- **`thread`** Nie można użyć atrybutu jako modyfikatora typu. Na przykład poniższy kod generuje błąd kompilatora:

    ```C
    char __declspec( thread ) *ch;        // Error
    ```

- Ponieważ deklaracja obiektów języka C++, które używają **`thread`** atrybutu jest dozwolona, następujące dwa przykłady są semantycznie równoważne:

    ```cpp
    __declspec( thread ) class B
    {
    // Code
    } BObject;  // OK--BObject is declared thread local.

    class B
    {
    // Code
    };
    __declspec( thread ) B BObject;  // OK--BObject is declared thread local.
    ```

- Adres lokalnego obiektu wątku nie jest uważany za stałą, a każde wyrażenie, w którym znajduje się taki adres, nie jest uważane za wyrażenie stałe. W standardowym języku C efektem jest niedozwolone użycie adresu zmiennej lokalnej wątku jako inicjatora dla obiektu lub wskaźnika. Na przykład następujący kod jest oflagowany jako błąd w kompilatorze języka C:

    ```C
    __declspec( thread ) int tls_i;
    int *p = &tls_i;       //This will generate an error in C.
    ```

   To ograniczenie nie ma zastosowania w języku C++. Ponieważ C++ pozwala na dynamiczną inicjalizację wszystkich obiektów, można zainicjować obiekt za pomocą wyrażenia, które używa adresu zmiennej lokalnej wątku. Jest to wykonywane podobnie jak konstrukcja obiektów lokalnych wątków. Na przykład przedstawiony wcześniej kod nie generuje błędu, gdy jest kompilowany jako plik źródłowy języka C++. Adres zmiennej lokalnej wątku jest prawidłowy tylko pod warunkiem, że wątek, w którym został pobrany, nadal istnieje.

- Standard C pozwala na inicjalizację obiektu lub zmiennej za pomocą wyrażenia, które obejmuje odwołanie do samego siebie, ale tylko dla obiektów niestatycznych. Chociaż język C++ ogólnie zezwala na takie dynamiczne inicjowanie obiektów z wyrażeniem, które obejmuje odwołanie do samego siebie, ten rodzaj inicjalizacji nie jest dozwolony w przypadku obiektów lokalnych wątków. Na przykład:

    ```C
    __declspec( thread )int tls_i = tls_i;                // Error in C and C++
    int j = j;                               // OK in C++, error in C
    __declspec( thread )int tls_i = sizeof( tls_i )       // Legal in C and C++
    ```

   **`sizeof`** Wyrażenie, które zawiera inicjowany obiekt nie reprezentuje odwołania do samego siebie i jest włączone zarówno w C, jak i C++.

   Język C++ nie pozwala na takie dynamiczne inicjowanie danych wątku ze względu na możliwe przyszłe ulepszenia funkcji lokalnego magazynu wątków.

- W systemach operacyjnych Windows przed systemem Windows Vista `__declspec( thread )` ma pewne ograniczenia. Jeśli biblioteka DLL deklaruje wszystkie dane lub obiekty jako `__declspec( thread )` , może to spowodować błąd ochrony w przypadku dynamicznego ładowania. Po załadowaniu biblioteki DLL przy użyciu funkcji [LoadLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryw), powoduje to awarię systemu zawsze wtedy, gdy kod odwołuje się do `__declspec( thread )` danych. Ze względu na to, że globalna przestrzeń zmienna dla wątku jest alokowana w czasie wykonywania, rozmiar tego miejsca jest oparty na obliczaniu wymagań aplikacji i wymaganiach wszystkich bibliotek DLL, które są połączone statycznie. Gdy używasz `LoadLibrary` , nie możesz zwiększyć tego miejsca, aby zezwolić na zmienne lokalne wątku zadeklarowane z `__declspec( thread )` . Użyj interfejsów API protokołu TLS, takich jak [Funkcja TlsAlloc](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsalloc), w bibliotece DLL do alokowania protokołu TLS, jeśli biblioteka DLL może zostać załadowana przy użyciu programu `LoadLibrary` .

## <a name="see-also"></a>Zobacz także

[Wielowątkowość z językiem C i podsystemem Win32](multithreading-with-c-and-win32.md)
