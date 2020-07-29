---
title: Atrybuty IDL (C++ COM)
ms.date: 10/02/2018
helpviewer_keywords:
- attributes [C++/CLI], reference topics
- IDL attributes
- .idl files [C++], attributes
- IDL files [C++], attributes
- .idl files [C++]
ms.assetid: 04c596f4-c97b-4952-8053-316678b1d0b6
ms.openlocfilehash: 8cceae2f1c4880b72f1ffc30070d6aa6bf8e3a51
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211973"
---
# <a name="idl-attributes"></a>atrybuty IDL

Tradycyjnie należy zachować plik. idl, który musiał:

- Zapoznaj się ze strukturą i składnią pliku. idl, aby móc go modyfikować.

- Polegaj na kreatorze, który umożliwia modyfikowanie niektórych aspektów pliku IDL.

Teraz można zmodyfikować plik IDL z pliku kodu źródłowego przy użyciu atrybutów Visual C++ IDL. W wielu przypadkach atrybuty Visual C++ IDL mają taką samą nazwę jak atrybuty MIDL. Gdy nazwa atrybutu Visual C++ IDL i atrybut MIDL są takie same, oznacza to, że umieszczenie atrybutu Visual C++ w pliku kodu źródłowego spowoduje, że plik IDL zawiera jego atrybut Namesake MIDL. Jednak atrybut Visual C++ IDL nie może udostępniać wszystkich funkcji atrybutu MIDL.

Jeśli nie jest używany z [atrybutami com](com-attributes.md), atrybuty IDL umożliwiają definiowanie interfejsów. Po skompilowaniu kodu źródłowego atrybuty są używane do definiowania wygenerowanego pliku IDL. Gdy jest używany z atrybutami COM w projekcie ATL, niektóre atrybuty IDL, takie jak `coclass` , powodują iniekcję kodu do projektu.

Należy pamiętać, że [idl_quote](idl-quote.md) umożliwia korzystanie z konstrukcji MIDL, które nie są obsługiwane w bieżącej wersji Visual C++. Te i inne atrybuty, takie jak [importlib](importlib.md) i [includelib —](includelib-cpp.md) , ułatwiają używanie istniejących plików IDL w bieżącym projekcie języka Visual Studio C++.

|Atrybut|Opis|
|---------------|-----------------|
|[aggregatable](aggregatable.md)|Wskazuje, że formant może być agregowany przez inną kontrolkę.|
|[appobject](appobject.md)|Identyfikuje klasę coclass jako obiekt aplikacji, która jest skojarzona z aplikacją z pełnym rozszerzeniem EXE i wskazuje, że funkcje i właściwości klasy coclass są dostępne globalnie w tej bibliotece typów.|
|[async_uuid](async-uuid.md)|Określa identyfikator UUID, który kieruje kompilator MIDL do definiowania synchronicznych i asynchronicznych wersji interfejsu COM.|
|[bindable](bindable.md)|Wskazuje, że właściwość obsługuje powiązanie danych.|
|[call_as](call-as.md)|Umożliwia zamapowanie funkcji niezdalnych na funkcję zdalną.|
|[spraw](case-cpp.md)|Używany z atrybutem [switch_type](switch-type.md) w Unii.|
|[coclass](coclass.md)|Umieszcza definicję klasy w pliku IDL jako klasy coclass.|
|[kontroli](control.md)|Określa, że typem zdefiniowanym przez użytkownika jest kontrolka.|
|[cpp_quote](cpp-quote.md)|Emituje określony ciąg bez znaków cudzysłowu do wygenerowanego pliku nagłówkowego.|
|[defaultbind](defaultbind.md)|Wskazuje pojedynczą, możliwą do powiązania właściwość, która najlepiej reprezentuje obiekt.|
|[defaultcollelem](defaultcollelem.md)|Używane do optymalizacji kodu Visual Basic.|
|[defaultvalue](defaultvalue.md)|Umożliwia określenie wartości domyślnej dla wpisanego parametru opcjonalnego.|
|[default](default-cpp.md)|Wskazuje, że niestandardowe lub dispinterface zdefiniowane w ramach klasy coclass reprezentuje domyślny interfejs programistyczny.|
|[defaultvtable](defaultvtable.md)|Definiuje interfejs jako domyślny interfejs tablicy metod dla kontrolki.|
|[dispinterface](dispinterface.md)|Umieszcza interfejs w pliku. idl jako interfejs wysyłania.|
|[displaybind](displaybind.md)|Wskazuje właściwość, która powinna być wyświetlana użytkownikowi jako możliwy do powiązania.|
|[dual](dual.md)|Umieszcza interfejs w pliku. idl jako podwójny interfejs.|
|[Autotekstu](entry.md)|Określa wyeksportowaną funkcję lub stałą w module, identyfikując punkt wejścia w bibliotece DLL.|
|[first_is](first-is.md)|Określa indeks pierwszego elementu tablicy, który ma zostać przesłany.|
|[helpcontext](helpcontext.md)|Określa identyfikator kontekstu, który umożliwia użytkownikowi wyświetlanie informacji o tym elemencie w pliku pomocy.|
|[helpfile](helpfile.md)|Ustawia nazwę pliku pomocy dla biblioteki typów.|
|[helpstringcontext](helpstringcontext.md)|Określa identyfikator tematu pomocy w pliku HLP lub chm.|
|[helpstringdll](helpstringdll.md)|Określa nazwę biblioteki DLL, która ma być używana do przeszukiwania ciągu dokumentu (lokalizacja).|
|[helpstring](helpstring.md)|Określa ciąg znaków, który jest używany do opisania elementu, do którego ma zastosowanie.|
|[hidden](hidden.md)|Wskazuje, że element istnieje, ale nie powinien być wyświetlany w przeglądarce zorientowanej na użytkownika.|
|[idl_module](idl-module.md)|Określa punkt wejścia w bibliotece DLL.|
|[idl_quote](idl-quote.md)|Umożliwia korzystanie z atrybutów lub konstrukcji IDL, które nie są obsługiwane w bieżącej wersji Visual C++.|
|[id](id.md)|Określa identyfikator DISPID dla funkcji składowej (właściwości lub metody w interfejsie lub dispinterface).|
|[iid_is](iid-is.md)|Określa identyfikator IID interfejsu COM wskazywanego przez wskaźnik interfejsu.|
|[immediatebind](immediatebind.md)|Wskazuje, że baza danych zostanie natychmiast powiadomiona o wszystkich zmianach właściwości obiektu powiązanego z danymi.|
|[importlib](importlib.md)|Sprawia, że typy, które zostały już skompilowane w innej bibliotece typów dostępne dla tworzonej biblioteki typów.|
|[zaimportować](import.md)|Określa inny plik IDL, ODL lub nagłówkowy zawierający definicje, które chcesz odwołać z głównego pliku. idl.|
|[być](include-cpp.md)|Określa co najmniej jeden plik nagłówka do uwzględnienia w wygenerowanym pliku IDL.|
|[includelib —](includelib-cpp.md)|Powoduje, że plik IDL lub h zostanie uwzględniony w wygenerowanym pliku IDL.|
|[in](in-cpp.md)|Wskazuje, że parametr ma być przekazywać z procedury wywołującej do procedury wywoływanej.|
|[last_is](last-is.md)|Określa indeks ostatniego elementu tablicy, który ma zostać przesłany.|
|[lcid](lcid.md)|Umożliwia przekazanie identyfikatora ustawień regionalnych do funkcji.|
|[length_is](length-is.md)|Określa liczbę elementów tablicy do przesłania.|
|[licensed](licensed.md)|Wskazuje, że Klasa coclass, do której ma zastosowanie, jest licencjonowana i musi być utworzona przy użyciu `IClassFactory2` .|
|[LAN](local-cpp.md)|Umożliwia użycie kompilatora MIDL jako generatora nagłówka, gdy jest używany w nagłówku interfejsu. W przypadku użycia w pojedynczej funkcji określa procedurę lokalną, dla której nie są generowane żadne wycinki.|
|[max_is](max-is.md)|Określa maksymalną wartość prawidłowego indeksu tablicy.|
|[elementu](module-cpp.md)|Definiuje blok biblioteki w pliku IDL.|
|[ms_union](ms-union.md)|Kontroluje wyrównanie danych sieci do wyrównania niehermetyzowanych Unii.|
|[no_injected_text](no-injected-text.md)|Uniemożliwia kompilatorowi wstrzyknięcie kodu w wyniku użycia atrybutów.|
|[nonbrowsable](nonbrowsable.md)|Wskazuje, że element członkowski interfejsu nie powinien być wyświetlany w przeglądarce właściwości.|
|[noncreatable](noncreatable.md)|Definiuje obiekt, którego nie można utworzyć na podstawie samego siebie.|
|[nonextensible](nonextensible.md)|Określa, że `IDispatch` implementacja zawiera tylko właściwości i metody wymienione w opisie interfejsu i nie można go rozszerzyć z dodatkowymi elementami członkowskimi w czasie wykonywania.|
|[object](object-cpp.md)|Identyfikuje niestandardowy interfejs; synonim z atrybutem niestandardowym.|
|[odl](odl.md)|Identyfikuje interfejs jako interfejs ODL (Object Description Language).|
|[oleautomation](oleautomation.md)|Wskazuje, że interfejs jest zgodny z automatyzacją.|
|[obowiązkowe](optional-cpp.md)|Określa opcjonalny parametr funkcji składowej.|
|[określoną](out-cpp.md)|Identyfikuje parametry wskaźnika, które są zwracane z wywoływanej procedury do procedury wywołującej (z serwera do klienta).|
|[pointer_default](pointer-default.md)|Określa domyślny atrybut wskaźnika dla wszystkich wskaźników oprócz wskaźników najwyższego poziomu, które są wyświetlane na listach parametrów.|
|[pragma](pragma.md)|Emituje określony ciąg bez znaków cudzysłowu do wygenerowanego pliku IDL.|
|[progid](progid.md)|Określa identyfikator ProgID dla obiektu COM.|
|[propget](propget.md)|Określa funkcję metody dostępu do właściwości (Get).|
|[propputref](propputref.md)|Określa funkcję ustawienia właściwości, która używa odwołania zamiast wartości.|
|[propput](propput.md)|Określa funkcję ustawienia właściwości.|
|[ptr](ptr.md)|Wyznacza wskaźnik jako pełny wskaźnik.|
|[public](public-cpp-attributes.md)|Zapewnia, że element typedef przejdzie do biblioteki typów, nawet jeśli nie jest przywoływany w pliku. idl.|
|[zakresu](range-cpp.md)|Określa zakres dozwolonych wartości dla argumentów lub pól, których wartości są ustawiane w czasie wykonywania.|
|[readonly](readonly-cpp.md)|Zabrania przypisywania do zmiennej.|
|[ref](ref-cpp.md)|Identyfikuje wskaźnik odwołania.|
|[requestedit](requestedit.md)|Wskazuje, że właściwość obsługuje `OnRequestEdit` powiadomienie.|
|[podlega](restricted.md)|Określa, że biblioteka lub element członkowski modułu, interfejsu lub dispinterface nie może zostać wywołany arbitralnie.|
|[retval](retval.md)|Określa parametr, który odbiera wartość zwracaną przez element członkowski.|
|[size_is](size-is.md)|Określa rozmiar pamięci przydzieloną dla wskaźników rozmiaru, wskaźniki rozmiaru do wskaźników rozmiaru i tablic pojedynczych lub wielowymiarowych.|
|[zewnętrz](source-cpp.md)|Wskazuje, że element członkowski klasy, właściwości lub metody jest źródłem zdarzeń.|
|[parametry](string-cpp.md)|Wskazuje, że tablica Jednowymiarowa **`char`** ,, **`wchar_t`** `byte` lub równoważna lub wskaźnik do takiej tablicy musi być traktowana jako ciąg.|
|[switch_is](switch-is.md)|Określa wyrażenie lub identyfikator działający jako discriminant Unii, który wybiera element członkowski Union.|
|[switch_type](switch-type.md)|Określa typ zmiennej używanej jako discriminant Unii.|
|[transmit_as](transmit-as.md)|Instruuje kompilator, aby skojarzyć przedstawiony typ, który obsługuje aplikacje klienta i serwera, z przesyłanym typem.|
|[uidefault](uidefault.md)|Wskazuje, że element członkowski informacji o typie jest domyślnym elementem członkowskim do wyświetlania w interfejsie użytkownika.|
|[unique](unique-cpp.md)|Określa unikatowy wskaźnik.|
|[usesgetlasterror](usesgetlasterror.md)|Instruuje obiekt wywołujący, że jeśli wystąpi błąd podczas wywoływania tej funkcji, wywołujący może następnie wywołać, `GetLastError` Aby pobrać kod błędu.|
|[uuid](uuid-cpp-attributes.md)|Określa unikatowy identyfikator klasy lub interfejsu.|
|[v1_enum](v1-enum.md)|Określa, że określony typ wyliczeniowy ma być przekazywany jako jednostka 32-bitowa, a nie wartość domyślna 16-bitowa.|
|[vararg](vararg.md)|Określa, że funkcja przyjmuje zmienną liczbę argumentów.|
|[vi_progid](vi-progid.md)|Określa niezależną od wersji identyfikator ProgID.|
|[wire_marshal](wire-marshal.md)|Określa typ danych, który będzie używany do przesyłania zamiast typu danych specyficznego dla aplikacji.|

## <a name="see-also"></a>Zobacz także

[Atrybuty według grupy](attributes-by-group.md)
