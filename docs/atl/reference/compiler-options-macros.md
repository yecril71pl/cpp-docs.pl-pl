---
title: Makra opcji kompilatora | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
f1_keywords:
- _ATL_ALL_WARNINGS
- _ATL_APARTMENT_THREADED
- '_ATL_CSTRING_EXPLICIT_CONSTRUCTORS '
- _ATL_ENABLE_PTM_WARNING
- _ATL_FREE_THREADED
- _ATL_MULTI_THREADED
- _ATL_NO_AUTOMATIC_NAMESPACE
- _ATL_NO_COM_SUPPORT
- ATL_NO_VTABLE
- ATL_NOINLINE
- _ATL_SINGLE_THREADED
helpviewer_keywords:
- compiler options, macros
ms.assetid: a869adc6-b3de-4299-b040-9ae20b45f82c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f48abc864133849353aeccf82ea3eb9aab1edb5a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-options-macros"></a>Makra opcji kompilatora
Te makra kontrolowania kompilatora określonych funkcji.  
  
|||  
|-|-|  
|[_ATL_ALL_WARNINGS](#_atl_all_warnings)|Symbol, który umożliwia błędy w projektach przekonwertować z poprzednich wersji ATL.|  
|[_ATL_APARTMENT_THREADED —](#_atl_apartment_threaded)|Zdefiniuj użycie co najmniej jeden z obiektów wątkowości typu apartment.|  
|[_ATL_CSTRING_EXPLICIT_CONSTRUCTORS](#_atl_cstring_explicit_constructors)|Sprawia, że niektóre `CString` jawne jakiejkolwiek konwersji niezamierzone zapobieganie konstruktorów.|  
|[_ATL_ENABLE_PTM_WARNING](#_atl_enable_ptm_warning)|Zdefiniuj to makro, aby można było używać składni języka C++ standardowe zgodne, który generuje błąd kompilatora C4867 stosowania z systemem innym niż standardowej składni w celu zainicjowania wskaźnika do funkcji członkowskiej.|  
|[_ATL_FREE_THREADED —](#_atl_free_threaded)|Zdefiniuj użycie co najmniej jeden z obiektów wolnego lub neutralną wątków.|  
|[_ATL_MULTI_THREADED](#_atl_multi_threaded)|Symbol, który wskazuje projekt będzie mieć obiektów, które są oznaczone jako oba wolne lub neutralna. Makro [_atl_free_threaded —](#_atl_free_threaded) należy użyć.|  
|[_ATL_NO_AUTOMATIC_NAMESPACE](#_atl_no_automatic_namespace)|Symbol, który uniemożliwia użycie domyślnej przestrzeni nazw jako ATL.|  
|[_ATL_NO_COM_SUPPORT](#_atl_no_com_support)|Symbol, który uniemożliwia kodu związanego z modelu COM jest kompilowane z projektu.|  
|[ATL_NO_VTABLE](#atl_no_vtable)|Symbol, który uniemożliwia zainicjowanie Konstruktor i destruktor klasy vtable wskaźnika.|  
|[ATL_NOINLINE](#atl_noinline)|Symbol, który wskazuje funkcji nie może być wbudowane.|  
|[_ATL_SINGLE_THREADED —](#_atl_single_threaded)|Określenie, czy wszystkie obiekty używać pojedynczego modelu wątkowości.|  
  
##  <a name="_atl_all_warnings"></a>_ATL_ALL_WARNINGS  
 Symbol, który umożliwia błędy w projektach przekonwertować z poprzednich wersji ATL.  
  
```
#define _ATL_ALL_WARNINGS
```  
  
### <a name="remarks"></a>Uwagi  
 Przed Visual C++ .NET 2002 ATL wyłączone wiele ostrzeżeń i pozostawić je wyłączyć, aby ich nigdy nie jest wykazało w kodzie użytkownika. W szczególności:  
  
-   C4127 wyrażenie warunkowe jest stałą  
  
-   C4786 'Identyfikator': identyfikator został obcięty do "number" znaków w informacji debugowania  
  
-   C4201 użyto niestandardowego rozszerzenia: typ struct/union  
  
-   C4103 "filename": używany #pragma pack można zmienić wyrównania  
  
-   C4291 "deklaracją": nie pasującego operatora delete znaleziono; pamięć nie zostanie zwolniona, jeśli Inicjalizacja generuje wyjątek  
  
-   C4268 "identyfikator": "const" statyczne/globalne dane zainicjowano przy użyciu wygenerowanego przez kompilator domyślnego konstruktora, który wypełnił obiekt zerami  
  
-   Nieosiągalny kod C4702  
  
 W projektach przekonwertować z poprzednich wersji te ostrzeżenia dotyczące nadal są wyłączone przez nagłówki bibliotek.  
  
 Dodając następujący wiersz w pliku stdafx.h przed dołączeniem nagłówki bibliotek, można zmienić to zachowanie.  
  
 [!code-cpp[NVC_ATL_Utilities#97](../../atl/codesnippet/cpp/compiler-options-macros_1.h)]  
  
 Jeśli ta `#define` dodaniu nagłówki ATL zostaną zaktualizowane zachować stan ostrzeżenia, dzięki czemu nie są globalnie wyłączone (lub użytkownik jawnie wyłącza ostrzeżeń indywidualnych, aby je włączyć, nie).  
  
 Nowy projekt ma to `#define` domyślnie ustawione w pliku stdafx.h.  
  
##  <a name="_atl_apartment_threaded"></a>_ATL_APARTMENT_THREADED —  
 Zdefiniuj użycie co najmniej jeden z obiektów wątkowości typu apartment.  
  
```
_ATL_APARTMENT_THREADED
```  
  
### <a name="remarks"></a>Uwagi  
 Określa wątkowości typu apartment. Zobacz [określanie modelu wątkowości projektu](../../atl/specifying-the-threading-model-for-a-project-atl.md) dla innych wątków opcje, a [opcji, Kreator prostych obiektów ATL](../../atl/reference/options-atl-simple-object-wizard.md) opis wątkowość modele dostępne dla obiekt ATL.  
  
##  <a name="_atl_cstring_explicit_constructors"></a>_ATL_CSTRING_EXPLICIT_CONSTRUCTORS  
 Sprawia, że niektóre `CString` jawne jakiejkolwiek konwersji niezamierzone zapobieganie konstruktorów.  
  
```
_ATL_CSTRING_EXPLICIT_CONSTRUCTORS
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli to jest zdefiniowana, wszystkie konstruktory CString, które przyjmować jeden parametr są kompilowane z jawnym słowem kluczowym, co uniemożliwia niejawne konwersje argumentów wejściowych. Oznacza to, na przykład, że po zdefiniowaniu _unicode — Jeśli próba użycia char * ciągu jako argument konstruktora obiektu CString, spowoduje błąd kompilatora. Używanie tego makra w sytuacjach, w których należy uniemożliwić niejawne konwersje między typami wąskie i szeroki ciąg.  
  
 Za pomocą makra _t — na wszystkie argumenty ciągu konstruktora, można zdefiniować _ATL_CSTRING_EXPLICIT_CONSTRUCTORS i uniknąć błędów kompilacji, niezależnie od tego, czy _unicode — jest zdefiniowane.  
  
##  <a name="_atl_enable_ptm_warning"></a>_ATL_ENABLE_PTM_WARNING  
 Zdefiniuj to makro, aby wymusić użycie składni zgodne standard ANSI C++ dla wskaźnika do funkcji Członkowskich. Użycie tego makra spowoduje błąd kompilatora C4867 ma być generowany, gdy niestandardowa składnia jest używany w celu zainicjowania wskaźnika do funkcji członkowskiej.  
  
```
#define _ATL_ENABLE_PTM_WARNING
```  
  
### <a name="remarks"></a>Uwagi  
 Aby dopasować kompilatora Visual C++ ulepszone standard C++ zgodności zostały zmienione biblioteki ATL i MFC. Ze standardem ANSI C++ składnia wskaźnika do funkcji członkowskiej klasy powinna mieć `&CMyClass::MyFunc`.  
  
 Gdy [_ATL_ENABLE_PTM_WARNING](#_atl_enable_ptm_warning) nie zdefiniowano (w przypadku domyślna), ATL/MFC wyłącza błąd C4867 w makra map (mapy szczególnie wiadomości), aby kod, który został utworzony we wcześniejszych wersjach można kontynuować tworzenie jak poprzednio. W przypadku definiowania **_ATL_ENABLE_PTM_WARNING**, kodu powinny być zgodne standard C++.  
  
 Jednak niestandardowym formularzu jest przestarzała, więc należy przenieść istniejący kod C++ standardowej składni zgodne. Na przykład następujące czynności:  
  
 [!code-cpp[NVC_MFCListView#14](../../atl/reference/codesnippet/cpp/compiler-options-macros_2.cpp)]  
  
 Należy zmienić typ na:  
  
 [!code-cpp[NVC_MFCListView#11](../../atl/reference/codesnippet/cpp/compiler-options-macros_3.cpp)]  
  
 Należy pamiętać, że dla makra mapy, które dodać znaku "&", nie należy dodawać go ponownie w kodzie.  
  
##  <a name="_atl_free_threaded"></a>_ATL_FREE_THREADED —  
 Zdefiniuj użycie co najmniej jeden z obiektów wolnego lub neutralną wątków.  
  
```
_ATL_FREE_THREADED
```  
  
### <a name="remarks"></a>Uwagi  
 Określa wolnych wątków. Wolnych wątków jest równoważna z modelem typu apartment wielowątkowe. Zobacz [określanie modelu wątkowości projektu](../../atl/specifying-the-threading-model-for-a-project-atl.md) dla innych wątków opcje, a [opcji, Kreator prostych obiektów ATL](../../atl/reference/options-atl-simple-object-wizard.md) opis wątkowość modele dostępne dla obiekt ATL.  
  
##  <a name="_atl_multi_threaded"></a>_ATL_MULTI_THREADED  
 Symbol, który wskazuje projekt będzie mieć obiektów, które są oznaczone jako oba wolne lub neutralna.  
  
```
_ATL_MULTI_THREADED
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli ta ikona jest zdefiniowany, ATL będzie pobierać w kodzie, który będzie poprawnie synchronizujący dostęp do danych globalnych. Nowy kod powinien użyć równoważnych makra [_atl_free_threaded —](#_atl_free_threaded) zamiast tego.  
  
##  <a name="_atl_no_automatic_namespace"></a>_ATL_NO_AUTOMATIC_NAMESPACE  
 Symbol, który uniemożliwia użycie domyślnej przestrzeni nazw jako ATL.  
  
```
_ATL_NO_AUTOMATIC_NAMESPACE
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli ten symbol nie jest zdefiniowany, zostanie przeprowadzone w tym atlbase.h **za pomocą przestrzeni nazw ATL** domyślnie, który może prowadzić do konfliktów nazw. Aby tego uniknąć, należy zdefiniować tego symbolu.  
  
##  <a name="_atl_no_com_support"></a>_ATL_NO_COM_SUPPORT  
 Symbol, który uniemożliwia kodu związanego z modelu COM jest kompilowane z projektu.  
  
```
_ATL_NO_COM_SUPPORT```  
  
##  <a name="atl_no_vtable"></a>  ATL_NO_VTABLE  
 A symbol that prevents the vtable pointer from being initialized in the class's constructor and destructor.  
  
```
ATL_NO_VTABLE
```  
  
### Remarks  
 If the vtable pointer is prevented from being initialized in the class's constructor and destructor, the linker can eliminate the vtable and all of the functions to which it points. Expands to **__declspec(novtable)**.  
  
### Example  
 [!code-cpp[NVC_ATL_COM#53](../../atl/codesnippet/cpp/compiler-options-macros_4.h)]  
  
##  <a name="atl_noinline"></a>  ATL_NOINLINE  
 A symbol that indicates a function should not be inlined.  
  
```
    ATL_NOINLINE inline
    myfunction
 { ... }
```  
  
### Parameters  
 *myfunction*  
 The function that should not be inlined.  
  
### Remarks  
 Use this symbol if you want to ensure a function does not get inlined by the compiler, even though it must be declared as inline so that it can be placed in a header file. Expands to **__declspec(noinline)**.  
  
##  <a name="_atl_single_threaded"></a>  _ATL_SINGLE_THREADED  
 Define if all of your objects use the single threading model  
  
```
_ATL_SINGLE_THREADED —
```  
  
### Remarks  
 Specifies that the object always runs in the primary COM thread. See [Specifying the Project's Threading Model](../../atl/specifying-the-threading-model-for-a-project-atl.md) for other threading options, and [Options, ATL Simple Object Wizard](../../atl/reference/options-atl-simple-object-wizard.md) for a description of the threading models available for an ATL object.  
  
## See Also  
 [Macros](../../atl/reference/atl-macros.md)
