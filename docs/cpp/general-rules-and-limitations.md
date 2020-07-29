---
title: Ograniczenia i reguły ogólne
ms.date: 11/04/2016
ms.assetid: 6c48902d-4259-4761-95d4-e421d69aa050
ms.openlocfilehash: 8d21f627f461dce90af93ca5c1af8c4a28098539
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213414"
---
# <a name="general-rules-and-limitations"></a>Ograniczenia i reguły ogólne

**Specyficzne dla firmy Microsoft**

- Jeśli deklarujesz funkcję lub obiekt bez **`dllimport`** **`dllexport`** atrybutu or, funkcja lub obiekt nie jest uważany za część interfejsu dll. W związku z tym definicja funkcji lub obiektu musi być obecna w tym module lub w innym module tego samego programu. Aby uczynić funkcję lub obiektem w interfejsie DLL, należy zadeklarować definicję funkcji lub obiektu w innym module jako **`dllexport`** . W przeciwnym razie zostanie wygenerowany błąd konsolidatora.

   Jeśli zadeklarujesz funkcję lub obiekt z **`dllexport`** atrybutem, jego definicja musi pojawić się w pewnym module tego samego programu. W przeciwnym razie zostanie wygenerowany błąd konsolidatora.

- Jeśli pojedynczy moduł w programie zawiera **`dllimport`** **`dllexport`** deklaracje i dla tej samej funkcji lub obiektu, **`dllexport`** atrybut ma pierwszeństwo przed **`dllimport`** atrybutem. Jest jednak generowane ostrzeżenie kompilatora. Na przykład:

    ```cpp
    __declspec( dllimport ) int i;
    __declspec( dllexport ) int i;   // Warning; inconsistent;
                                     // dllexport takes precedence.
    ```

- W języku C++ można zainicjować globalnie zadeklarowany lub statyczny wskaźnik danych lokalnych lub z adresem obiektu danych zadeklarowanego za pomocą **`dllimport`** atrybutu, który generuje błąd w C. Ponadto można zainicjować statyczny wskaźnik funkcji lokalnych z adresem funkcji zadeklarowanej przy użyciu **`dllimport`** atrybutu. W języku C takie przypisanie ustawia wskaźnik na adres biblioteki DLL thunk (Kod zastępczy, który przekazuje kontrolę do funkcji), a nie adres funkcji. W języku C++ ustawia wskaźnik na adres funkcji. Na przykład:

    ```cpp
    __declspec( dllimport ) void func1( void );
    __declspec( dllimport ) int i;

    int *pi = &i;                             // Error in C
    static void ( *pf )( void ) = &func1;     // Address of thunk in C,
                                              // function in C++

    void func2()
    {
       static int *pi = &i;                  // Error in C
       static void ( *pf )( void ) = &func1; // Address of thunk in C,
                                             // function in C++
    }
    ```

   Jednak ponieważ program, który zawiera **`dllexport`** atrybut w deklaracji obiektu, musi podać definicję dla tego obiektu w programie, można zainicjować globalny lub lokalny wskaźnik funkcji statycznej przy użyciu adresu **`dllexport`** funkcji. Analogicznie, można zainicjować globalny lub lokalny wskaźnik danych statycznych o adresie **`dllexport`** obiektu danych. Na przykład następujący kod nie generuje błędów w C lub C++:

    ```cpp
    __declspec( dllexport ) void func1( void );
    __declspec( dllexport ) int i;

    int *pi = &i;                              // Okay
    static void ( *pf )( void ) = &func1;      // Okay

    void func2()
    {
        static int *pi = &i;                   // Okay
        static void ( *pf )( void ) = &func1;  // Okay
    }
    ```

- W przypadku zastosowania **`dllexport`** do zwykłej klasy, która ma klasę bazową, która nie jest oznaczona jako **`dllexport`** , kompilator generuje C4275.

   Kompilator generuje to samo ostrzeżenie, jeśli klasa bazowa jest specjalizacją szablonu klasy. Aby obejść ten krok, Oznacz klasę podstawową za pomocą **`dllexport`** . Problem z specjalizacją szablonu klasy jest miejscem, w którym należy umieścić **`__declspec(dllexport)`** ; nie można oznaczyć szablonu klasy. Zamiast tego należy jawnie utworzyć wystąpienie szablonu klasy i oznaczyć to jawne wystąpienie z **`dllexport`** . Na przykład:

    ```cpp
    template class __declspec(dllexport) B<int>;
    class __declspec(dllexport) D : public B<int> {
    // ...
    ```

   To obejście nie powiedzie się, jeśli argument szablonu jest klasą pochodną. Na przykład:

    ```cpp
    class __declspec(dllexport) D : public B<D> {
    // ...
    ```

   Ponieważ jest to typowy wzorzec z szablonami, kompilator zmienił semantykę, **`dllexport`** gdy jest stosowana do klasy, która ma co najmniej jedną klasę bazową, a co najmniej jedna z klas bazowych jest specjalizacją szablonu klasy. W tym przypadku kompilator niejawnie stosuje się **`dllexport`** do specjalizacji szablonów klas. Można wykonać następujące czynności i nie otrzymać ostrzeżenia:

    ```cpp
    class __declspec(dllexport) D : public B<D> {
    // ...
    ```

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[dllexport, dllimport](../cpp/dllexport-dllimport.md)
