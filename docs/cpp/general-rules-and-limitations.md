---
title: Ograniczenia i reguły ogólne | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 6c48902d-4259-4761-95d4-e421d69aa050
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 51f92844e993671a3423c04523ccf4e03f7f7e48
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="general-rules-and-limitations"></a>Ograniczenia i reguły ogólne
## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft  
  
-   W przypadku zadeklarowania funkcji lub obiekt bez **dllimport** lub `dllexport` atrybutu, funkcji lub obiekt nie jest uznawany za część interfejsu biblioteki DLL. W związku z tym definicji funkcji lub obiektu musi być obecne w module lub w innym module ten sam program. Aby funkcja lub obiekt część interfejsu biblioteki DLL, muszą deklarować definicji funkcji lub obiekt w module jako `dllexport`. W przeciwnym razie zostanie wygenerowany błąd konsolidatora.  
  
     W przypadku zadeklarowania funkcji lub obiekt z `dllexport` atrybutu i jego definicji musi występować w niektórych moduł ten sam program. W przeciwnym razie zostanie wygenerowany błąd konsolidatora.  
  
-   Jeśli pojedynczy moduł w programie zawiera zarówno **dllimport** i `dllexport` deklaracje dla tej samej funkcji lub obiektu, `dllexport` atrybut ma pierwszeństwo przed **dllimport** atrybut. Jednak generowania ostrzeżeń kompilatora. Na przykład:  
  
    ```  
    __declspec( dllimport ) int i;  
    __declspec( dllexport ) int i;   // Warning; inconsistent;  
                                     // dllexport takes precedence.  
    ```  
  
-   W języku C++ może zainicjować wskaźnik globalnie zadeklarowane lub statycznych danych lokalnych lub z adresem obiektu danych zadeklarowana z **dllimport** atrybut, który generuje błąd w C. Ponadto można zainicjować wskaźnik statycznej funkcji lokalny adres funkcja zadeklarowana z **dllimport** atrybutu. W języku C takiego przypisania ustawia wskaźnik do adresu thunk importu biblioteki DLL (Kod szczątkowy, przesyłania funkcji sterowania) zamiast adresu funkcji. W języku C++ ustawia wskaźnik adres funkcji. Na przykład:  
  
    ```  
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
  
     Jednakże ponieważ program, który zawiera `dllexport` atrybutu w deklaracji obiektu musi podać definicję dla tego obiektu w programie, należy zainicjować wskaźnik statycznej funkcji globalnych lub lokalnych z adresem `dllexport`funkcji. Podobnie można zainicjować wskaźnik globalnych lub lokalnych danych statycznych adres `dllexport` obiektu danych. Na przykład następujący kod nie generuje błędy w języka C lub C++:  
  
    ```  
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
  
-   W przypadku zastosowania `dllexport` regularne klasę, która ma klasy podstawowej, która nie jest oznaczona jako `dllexport`, kompilator wygeneruje C4275.  
  
     Kompilator generuje tego samego ostrzeżenie, jeśli klasą podstawową jest specjalizacją szablonu klasy. Aby obejść ten problem, oznaczenie klasy podstawowej z `dllexport`. Problem z specjalizacji szablonu klasy jest lokalizację **__declspec(dllexport)**; nie możesz oznaczyć szablonu klasy. Zamiast tego należy jawnie utworzyć wystąpienia szablonu klasy i oznacz ten jawne utworzenie wystąpienia z `dllexport`. Na przykład:  
  
    ```  
    template class __declspec(dllexport) B<int>;  
    class __declspec(dllexport) D : public B<int> {  
    // ...  
    ```  
  
     To rozwiązanie nie powiedzie się, jeśli Klasa pochodna jest argument szablonu. Na przykład:  
  
    ```  
    class __declspec(dllexport) D : public B<D> {  
    // ...  
    ```  
  
     Ponieważ jest to wspólnego wzorca z szablonami, kompilator zmienić semantykę `dllexport` po zastosowaniu do klasy, która ma co najmniej jednej klasy podstawowej i co najmniej jeden z klas podstawowych jest specjalizacją szablonu klasy. W tym przypadku kompilator niejawnie dotyczy `dllexport` dla specjalizacji klasy szablonów. Można wykonać następujące czynności i nie można uzyskać Ostrzeżenie:  
  
    ```  
    class __declspec(dllexport) D : public B<D> {  
    // ...  
    ```  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [dllexport, dllimport](../cpp/dllexport-dllimport.md)