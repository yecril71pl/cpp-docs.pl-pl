---
title: Ograniczenia i reguły ogólne | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 6c48902d-4259-4761-95d4-e421d69aa050
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0222af4bd53b21750cb6debc477e10c96f9d5594
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50061589"
---
# <a name="general-rules-and-limitations"></a>Ograniczenia i reguły ogólne

## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft

- W przypadku deklarowania funkcji lub obiektu bez **dllimport** lub **dllexport** atrybutu, funkcji lub obiektu nie jest uważany za część interfejsu biblioteki DLL. W związku z tym definicja funkcji lub obiektu musi być obecny, w tym module lub w innym module tego samego programu. Aby funkcji lub obiektu częścią interfejsu biblioteki DLL, należy zadeklarować definicji funkcji lub obiektu w module jako **dllexport**. W przeciwnym razie zostanie wygenerowany błąd konsolidatora.

   W przypadku deklarowania funkcji lub obiekt z **dllexport** atrybutu, jego definicja musi znajdować się w niektórych module tego samego programu. W przeciwnym razie zostanie wygenerowany błąd konsolidatora.

- Jeśli pojedynczy moduł w programie zawiera zarówno **dllimport** i **dllexport** deklaracje dla tej samej funkcji lub obiektu, **dllexport** pierwszeństwo atrybutów za pośrednictwem **dllimport** atrybutu. Jednak kompilator wygeneruje ostrzeżenie. Na przykład:

    ```cpp
    __declspec( dllimport ) int i;
    __declspec( dllexport ) int i;   // Warning; inconsistent;
                                     // dllexport takes precedence.
    ```

- W języku C++, można zainicjować wskaźnik globalnie zadeklarowane lub statycznych danych lokalnych lub przy użyciu adresu obiektu danych zadeklarowane za pomocą **dllimport** atrybut, który generuje błąd w C. Ponadto można zainicjować wskaźnik statycznych funkcji lokalnych przy użyciu adresu funkcja zadeklarowana za pomocą **dllimport** atrybutu. W języku C takie przypisania ustawia wskaźnik na adres thunk importu biblioteki DLL (kod odcinek, który przekazuje sterowanie do funkcji) zamiast adresu funkcji. W języku C++ ustawia wskaźnik do adresu funkcji. Na przykład:

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

   Jednak ponieważ program, który zawiera **dllexport** atrybutu w deklaracji obiektu, należy podać definicję dla tego obiektu gdzieś w programie, można zainicjować wskaźnik statycznej funkcji globalnych lub lokalnych za pomocą adres **dllexport** funkcji. Podobnie, można zainicjować wskaźnik globalnych lub lokalnych danych statycznych, adresem **dllexport** obiektu danych. Na przykład poniższy kod generuje błędy w C lub C++:

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

- Jeśli zastosujesz **dllexport** do regularnego klasy, która ma klasę bazową, która nie jest oznaczona jako **dllexport**, kompilator wygeneruje C4275.

   Kompilator generuje ostrzeżenie o tym samym, jeśli klasa bazowa jest specjalizacją szablonu klasy. Aby obejść ten problem, należy oznaczyć klasy podstawowej za pomocą **dllexport**. Problem z specjalizacji szablonu klasy jest gdzie umieścić **__declspec(dllexport)**; oznaczyć szablon klasy jest niedozwolone. Zamiast tego należy jawnie tworzenia wystąpienia szablonu klasy i oznaczyć to jawne utworzenie wystąpienia z **dllexport**. Na przykład:

    ```cpp
    template class __declspec(dllexport) B<int>;
    class __declspec(dllexport) D : public B<int> {
    // ...
    ```

   To rozwiązanie nie powiedzie się, jeśli argument szablonu jest klasa pochodna. Na przykład:

    ```cpp
    class __declspec(dllexport) D : public B<D> {
    // ...
    ```

   Ponieważ jest to typowy wzorzec przy użyciu szablonów, kompilator zmienione semantykę **dllexport** po zastosowaniu do klasy, która ma jeden lub więcej klas podstawowych i co najmniej jedna z klas bazowych jest specjalizacją szablonu klasy . W tym przypadku kompilator stosuje niejawnie **dllexport** aby specjalizacje szablonów klas. Można wykonać następujące czynności i nie wyświetlone ostrzeżenie:

    ```cpp
    class __declspec(dllexport) D : public B<D> {
    // ...
    ```

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[dllexport, dllimport](../cpp/dllexport-dllimport.md)