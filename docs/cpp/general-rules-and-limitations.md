---
title: Ograniczenia i reguły ogólne
ms.date: 11/04/2016
ms.assetid: 6c48902d-4259-4761-95d4-e421d69aa050
ms.openlocfilehash: 3bd8956b08d3e5f2109c5574802a3a8a72fba537
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857531"
---
# <a name="general-rules-and-limitations"></a>Ograniczenia i reguły ogólne

**Microsoft Specific**

- Jeśli zadeklarujesz funkcję lub obiekt bez atrybutu **dllimport** lub **dllexport** , funkcja lub obiekt nie jest uważany za część interfejsu dll. W związku z tym definicja funkcji lub obiektu musi być obecna w tym module lub w innym module tego samego programu. Aby uczynić funkcję lub obiektem w interfejsie DLL, należy zadeklarować definicję funkcji lub obiektu w innym module jako **dllexport**. W przeciwnym wypadku zostanie wygenerowany błąd konsolidatora.

   Jeśli deklarujesz funkcję lub obiekt z atrybutem **dllexport** , jego definicja musi znajdować się w pewnym module tego samego programu. W przeciwnym wypadku zostanie wygenerowany błąd konsolidatora.

- Jeśli pojedynczy moduł w programie zawiera deklaracje **dllimport** i **dllexport** dla tej samej funkcji lub obiektu, atrybut **dllexport** ma pierwszeństwo przed atrybutem **dllimport** . Jest jednak generowane ostrzeżenie kompilatora. Na przykład:

    ```cpp
    __declspec( dllimport ) int i;
    __declspec( dllexport ) int i;   // Warning; inconsistent;
                                     // dllexport takes precedence.
    ```

- W C++programie można zainicjować globalnie zadeklarowany lub statyczny wskaźnik danych lokalnych lub z adresem obiektu danych zadeklarowanego za pomocą atrybutu **dllimport** , który generuje błąd w C. Ponadto można zainicjować statyczny wskaźnik funkcji lokalnych przy użyciu adresu funkcji zadeklarowanej z atrybutem **dllimport** . W języku C takie przypisanie ustawia wskaźnik na adres biblioteki DLL thunk (Kod zastępczy, który przekazuje kontrolę do funkcji), a nie adres funkcji. W C++programie ustawia wskaźnik na adres funkcji. Na przykład:

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

   Jednak ponieważ program, który zawiera atrybut **dllexport** w deklaracji obiektu, musi podać definicję dla tego obiektu w programie, można zainicjować globalny lub lokalny wskaźnik funkcji statycznej przy użyciu adresu funkcji **dllexport** . Analogicznie, można zainicjować globalny lub lokalny wskaźnik danych statycznych z adresem obiektu danych **dllexport** . Na przykład następujący kod nie generuje błędów w C lub C++:

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

- Jeśli zastosujesz **dllexport** do zwykłej klasy, która ma klasę bazową, która nie jest oznaczona jako **dllexport**, kompilator wygeneruje C4275.

   Kompilator generuje to samo ostrzeżenie, jeśli klasa bazowa jest specjalizacją szablonu klasy. Aby obejść ten krok, Oznacz klasę bazową **dllexport**. Problem z specjalizacją szablonu klasy znajduje się w lokalizacji, w której ma zostać umieszczony **__declspec (dllexport)** ; nie można oznaczyć szablonu klasy. Zamiast tego należy jawnie utworzyć wystąpienie szablonu klasy i oznaczyć to jawne wystąpienie z **dllexport**. Na przykład:

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

   Ponieważ jest to typowy wzorzec z szablonami, kompilator zmienił semantykę **dllexport** , gdy jest stosowany do klasy, która ma co najmniej jedną klasę bazową, a co najmniej jedna z klas bazowych jest specjalizacją szablonu klasy. W takim przypadku kompilator niejawnie stosuje **dllexport** do specjalizacji szablonów klas. Można wykonać następujące czynności i nie otrzymać ostrzeżenia:

    ```cpp
    class __declspec(dllexport) D : public B<D> {
    // ...
    ```

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[dllexport, dllimport](../cpp/dllexport-dllimport.md)