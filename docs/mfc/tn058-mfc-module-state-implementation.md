---
title: 'TN058: implementacja stanu modułu MFC'
ms.date: 06/28/2018
f1_keywords:
- vc.mfc.implementation
helpviewer_keywords:
- thread state [MFC]
- module states [MFC], managing state data
- TN058
- MFC, managing state data
- module states [MFC], switching
- DLLs [MFC], module states
- process state [MFC]
ms.assetid: 72f5b36f-b3da-4009-a144-24258dcd2b2f
ms.openlocfilehash: db34f528e70a7dcc437836684656b3ce8a4078fd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50626052"
---
# <a name="tn058-mfc-module-state-implementation"></a>TN058: implementacja stanu modułu MFC

> [!NOTE]
> Następująca uwaga techniczna nie został zaktualizowany od pierwszego uwzględnienia jej w dokumentacji online. W rezultacie niektóre procedury i tematy może być nieaktualne lub niepoprawne. Najnowsze informacje zaleca się wyszukać temat w indeksie dokumentacji online.

Ta uwaga techniczna opisuje implementacja konstrukcji "Stanu modułu MFC". Po zrozumieniu implementacja stanu modułu ma kluczowe znaczenie, za pomocą MFC współużytkowanych bibliotek DLL z biblioteki DLL (lub OLE w procesie serwera).

Przed odczytaniem ta uwaga, odnoszą się do "Zarządzanie stanu danych z MFC — moduły" [tworzenie nowych dokumentów, Windows i widoki](../mfc/creating-new-documents-windows-and-views.md). Ten artykuł zawiera informacje o użyciu ważne i informacje na ten temat.

## <a name="overview"></a>Omówienie

Istnieją trzy rodzaje informacji o stanie MFC: stan modułu, stan procesu i stan wątku. Czasami można połączyć te typy stanu. Na przykład map uchwyt MFC są zarówno modułu lokalnych, jak i lokalnych wątku. Dzięki temu dwóch różnych modułach zapewnienie różnych mapowań w każdym z jego wątków.

Stan procesu i stan wątku są podobne. Te elementy danych są rzeczy, które zostały tradycyjnie zmiennych globalnych, ale mają należy specyficzne dla danego procesu lub wątek do właściwego systemach Win32 pomoc techniczną lub obsługa wielowątkowości w odpowiednie. Jakiej kategorii elementu danych mieści się w zależy od tego elementu i jego żądaną semantyki w odniesieniu do granic procesu i wątku.

Stan modułu jest unikatowa, w tym może zawierać prawdziwie globalna, stanu lub stan, który jest procesem lokalnym lub wątku lokalnego. Ponadto jego mogą być przełączane szybko.

## <a name="module-state-switching"></a>Przełączenie stanu modułu

Każdy wątek zawiera wskaźnik do stanu "bieżącej" lub "aktywny" modułu (nie zaskakująco wskaźnik jest częścią stan lokalnego wątku MFC). This, wskaźnik jest zmieniany, gdy wątek wykonywania przekazuje granicy modułu, takie jak aplikacja wywoływanie kontrolkę OLE lub biblioteki DLL lub formantu OLE wywołań zwrotnych do aplikacji.

Bieżący stan modułu jest włączane przez wywołanie metody `AfxSetModuleState`. W większości przypadków będzie nigdy nie dotyczą bezpośrednio z interfejsem API. MFC, w wielu przypadkach będzie wywoływać go dla Ciebie (po WinMain, OLE punkty wejścia, `AfxWndProc`itp.). Jest to wykonywane w jakikolwiek składnik zapisu łącząc statycznie w specjalnej `WndProc`i specjalny `WinMain` (lub `DllMain`) który wie, w określonym stanie modułu powinien być nieaktualne. Zostanie wyświetlony ten kod, analizując DLLMODUL. CPP lub APPMODUL. CPP w katalogu MFC\SRC.

Jest to rzadkie, że chcesz ustawić stan modułu i nie jest ustawiony ponownie. W większości przypadków ma swój własny moduł "push" stan jako bieżący, a następnie, po wykonaniu czynności "pop" ponownie oryginalnego kontekstu. Jest to realizowane przez makro [AFX_MANAGE_STATE](reference/extension-dll-macros.md#afx_manage_state) i klasy specjalnej `AFX_MAINTAIN_STATE`.

`CCmdTarget` zawiera specjalne funkcje do obsługi przełączania stanu modułu. W szczególności `CCmdTarget` jest główna klasa służy do automatyzacji OLE i OLE COM, punkty wejścia. Inne punkty wejścia, takie jak dostępne w systemie, te punkty wejścia, należy ustawić stan prawidłowy moduł. Jak jest dany `CCmdTarget` wiedzieć, jakie stanu modułu "poprawny" powinny być odpowiedź jest, że "pamięta" co "bieżący" Stan modułu jest, gdy jest tworzony, w taki sposób, że można ustawić bieżącego stanu modułu, "zapamiętanych" o nazwie wartość, gdy jest ona nowsza. W rezultacie moduł określają, że dany `CCmdTarget` obiekt jest skojarzony z jest stanu modułu, które były aktualne, gdy obiekt został zbudowany. Wykonaj prosty przykład ładowanie serwera INPROC, tworzenia obiektu i wywoływania jego metody.

1. Biblioteka DLL jest ładowany przez OLE przy użyciu `LoadLibrary`.

2. `RawDllMain` najpierw jest wywoływana. Ustawia stan modułu do stanu znanych moduł statycznej biblioteki dll. Z tego powodu `RawDllMain` łączone statycznie do biblioteki DLL.

1. Konstruktor dla fabryki klas, skojarzone z naszych obiektu jest wywoływana. `COleObjectFactory` jest tworzony na podstawie `CCmdTarget` co w efekcie pamięta w określonym stanie moduł został uruchomiony. Jest to ważne — poproszona fabrykę klas do tworzenia obiektów zna teraz który stan modułu Ustaw jako bieżącą.

4. `DllGetClassObject` jest wywoływana, aby otrzymać fabrykę klas. MFC wyszukuje listy fabryki klas, które są skojarzone z tym modułem i zwraca go.

5. `COleObjectFactory::XClassFactory2::CreateInstance` jest wywoływana. Przed utworzeniem obiektu i przywróceniem go, funkcja ta ustawia stan modułu stanu modułu, które były aktualne w kroku 3 (jeden, które były aktualne, kiedy `COleObjectFactory` wystąpienia). Odbywa się wewnątrz [METHOD_PROLOGUE](com-interface-entry-points.md).

1. Podczas tworzenia obiektu zbyt jest `CCmdTarget` pochodnych i tak samo jak `COleObjectFactory` zapamiętanych stanu modułu, który był aktywny, to samo dotyczy tego nowego obiektu. Teraz obiekt wie, których stan modułu, aby przełączyć się do zawsze, gdy jest wywoływana.

1. Klient wywołuje funkcję dla obiektu OLE COM, który otrzymał od jego `CoCreateInstance` wywołania. Gdy obiekt jest nazywany używa `METHOD_PROLOGUE` podobnie jak przełączyć stanu modułu `COleObjectFactory` jest.

Jak widać, stan modułu jest propagowany z obiektu do obiektu, ponieważ są one tworzone. Należy odpowiednio ustawić stanu modułu. Jeśli nie jest ustawiona, obiekt biblioteki DLL lub COM mogą wchodzić w interakcje źle z aplikacji MFC, która jest wywołanie, nie będą mogły odnaleźć swoich własnych zasobów lub może zakończyć się niepowodzeniem w inny sposób miserable.

Należy zauważyć pewne rodzaje bibliotek DLL, w szczególności biblioteki dll "Rozszerzeń MFC" nie Przełączaj stanu modułu w ich `RawDllMain` (w rzeczywistości zwykle nie mają nawet `RawDllMain`). Jest to spowodowane są przeznaczone do zachowują się "jak gdyby" faktycznie znajduje się w aplikacji, która korzysta z nich. Są one znacznie częścią aplikacji, która działa i jest ich zamiar zmiany stanu globalnego dla tej aplikacji.

Formanty OLE i inne biblioteki DLL są bardzo różne. Nie chcą zmodyfikować stanu aplikacji wywołującej; aplikacji, która je wywołuje nie może być nawet aplikacji MFC, a więc może istnieć bez stanu, aby zmodyfikować. Jest to powód, że przełączenie stanu modułu została opracowana.

Eksportowanych funkcji z biblioteki DLL, taki, który uruchamia okno dialogowe w bibliotece DLL należy dodać następujący kod na początku funkcji:

```cpp
AFX_MANAGE_STATE(AfxGetStaticModuleState())
```

Zamienia to bieżący stan modułu ze stanem zwróciło [AfxGetStaticModuleState —](reference/extension-dll-macros.md#afxgetstaticmodulestate) aż do końca bieżącego zakresu.

Problemy z zasobami w bibliotekach DLL występuje, jeśli makro afx_module_state — nie jest używany. Domyślnie MFC wykorzystuje uchwyt zasobów aplikacji głównej można załadować szablonu zasobów. Ten szablon rzeczywiście jest przechowywana w bibliotece DLL. Główną przyczyną jest informacje o stanie modułu MFC nie został przełączony przez afx_module_state — makro. Dojście do zasobu jest odzyskiwany od stanu modułu MFC. Nie przełączenie stanu modułu powoduje, że dojście niewłaściwych zasobów ma być używany.

Afx_module_state — nie musi znajdować się w każdej funkcji w bibliotece DLL. Na przykład `InitInstance` można wywoływać za pomocą kodu MFC w aplikacji bez afx_module_state — ponieważ MFC jest kierowany w stanie modułu przed `InitInstance` i następnie przełączników je z powrotem po `InitInstance` zwraca. Dotyczy to także wszystkie programy obsługi komunikatów mapy. Regularne biblioteki DLL MFC faktycznie istnieje procedura specjalne okna głównego, która automatycznie przełącza moduł przed przesłaniem wszystkie komunikaty.

## <a name="process-local-data"></a>Przetwarzanie danych lokalnych

Przetwarzanie danych lokalnych nie będą takie nas bardzo ważne, gdyby nie został dla trudności w systemach Win32 DLL modelu. W systemach Win32 wszystkich bibliotek DLLs udostępniać swoje dane globalne, nawet wtedy, gdy jest ładowany przez wiele aplikacji. Jest to bardzo różnią się od "członu real" model danych Win32 DLL, gdzie każdą bibliotekę DLL pobiera osobną kopię swojej przestrzeni danych w każdym procesie, który dołącza do biblioteki DLL. Aby dodać do złożoności, dane przydzielony na stosie w bibliotece DLL systemach Win32 są w rzeczywistości określonego procesu (co najmniej tyle co przechodzi własność). Należy wziąć pod uwagę następujące dane i kodu:

```cpp
static CString strGlobal; // at file scope

__declspec(dllexport)
void SetGlobalString(LPCTSTR lpsz)
{
    strGlobal = lpsz;
}

__declspec(dllexport)
void GetGlobalString(LPCTSTR lpsz, size_t cb)
{
    StringCbCopy(lpsz, cb, strGlobal);
}
```

Należy wziąć pod uwagę, co się stanie, jeśli powyższy kod w znajduje się w bibliotece DLL i ładowanie biblioteki DLL przy użyciu dwóch procesów, A i B (jej w rzeczywistości można dwa wystąpienia tej samej aplikacji). Wywołania `SetGlobalString("Hello from A")`. W rezultacie pamięć została przydzielona dla `CString` danych w ramach procesu pamiętać A. należy uwzględnić następujące kwestie `CString` sam jest globalna i jest widoczny dla obu A i B. Teraz wywołuje B `GetGlobalString(sz, sizeof(sz))`. B, będzie można wyświetlić dane, które Ustaw element. Jest to spowodowane systemach Win32 oferuje Brak ochrony między procesami, jak w Win32. To pierwszy problemu. w wielu przypadkach nie jest pożądane, aby jednej aplikacji, które mają wpływ na dane globalne, który jest uważany za należy do innej aplikacji.

Istnieją także dodatkowe problemy. Załóżmy, że teraz kończy działanie. Gdy A kończy działanie, pamięć używana przez "`strGlobal`" ciągu jest udostępniana dla systemu — czyli wszystkich pamięci przydzielonej przez proces A jest zwalniana automatycznie przez system operacyjny. Nie jest zwalniana, ponieważ `CString` destruktor jest wywoływana; nie została wywołana jeszcze. Zostanie zwolniona po prostu ponieważ aplikację, która przydzielona opuścił sceny. Teraz, jeśli wywołano B `GetGlobalString(sz, sizeof(sz))`, go nie zawierają prawidłowych danych. Inna aplikacja może użyto pamięci dla innego elementu.

Wyraźnie istnieje problem. MFC 3.x używane technikę o nazwie lokalny magazyn wątków (TLS). MFC 3.x czy przydzielić indeksu TLS, działającego w systemach Win32 naprawdę jako indeks proces lokalny magazyn, nawet jeśli nie zostanie wywołana i następnie będzie odwoływać się do wszystkich danych, w oparciu o indeksu TLS. Jest to podobne do indeksu TLS, który został użyty do przechowywania danych lokalnych wątków w Win32 (Aby uzyskać więcej informacji na ten temat zobacz poniżej). Spowodowało to każdej biblioteki DLL MFC, korzystanie z co najmniej dwóch TLS indeksów w procesie. Gdy uwzględnić wiele OLE kontroli bibliotek DLL ładowanych formanty (OCX), szybko wyczerpią się indeksów protokołu TLS (Brak dostępnych tylko 64). Ponadto MFC było umieścić te dane w jednym miejscu, struktura single. Nie można rozszerzyć bardzo, a nie jest idealnym rozwiązaniem w odniesieniu do sposobu korzystania z protokołu TLS indeksów.

MFC 4.x rozwiązuje ten zestaw szablonów klas, które użytkownik może "opakowuje" dane, które powinny być procesem lokalnym. Na przykład problem, o których wspomniano powyżej, może zostać naprawione przez napisanie:

```cpp
struct CMyGlobalData : public CNoTrackObject
{
    CString strGlobal;
};
CProcessLocal<CMyGlobalData> globalData;

__declspec(dllexport)
void SetGlobalString(LPCTSTR lpsz)
{
    globalData->strGlobal = lpsz;
}

__declspec(dllexport)
void GetGlobalString(LPCTSTR lpsz, size_t cb)
{
    StringCbCopy(lpsz, cb, globalData->strGlobal);
}
```

MFC implementuje to w dwóch krokach. Po pierwsze, jest warstwą Win32 __Tls\*__  interfejsy API (**TlsAlloc**, **TlsSetValue**, **TlsGetValue**itd) który tylko dwa indeksów protokołu TLS na proces, niezależnie od tego, jak wiele bibliotek DLL, należy użyć. Drugi `CProcessLocal` szablon znajduje się na dostęp do tych danych. Zastępuje ona operator ->, który jest, co umożliwia intuicyjne składni, zobacz powyżej. Wszystkie obiekty, które zostaną opakowane przy `CProcessLocal` musi pochodzić od `CNoTrackObject`. `CNoTrackObject` udostępnia alokatora niższego poziomu (**Funkcja LocalAlloc**/**LocalFree**) i destruktor wirtualny tak, aby MFC automatycznie może zniszczyć lokalne obiekty procesu, gdy proces zostanie zakończony. Takie obiekty mogą mieć niestandardowe destruktor, jeśli wymagane jest dodatkowe oczyszczanie. Powyższy przykład nie wymaga jednego, ponieważ kompilator wygeneruje domyślny destruktor zniszczyć osadzonego `CString` obiektu.

Istnieją inne interesujące zalety tego podejścia. Są nie tylko wszystkie `CProcessLocal` obiektów zniszczone automatycznie, które nie są zbudowane dopóki nie są potrzebne. `CProcessLocal::operator->` będzie tworzy skojarzonego obiektu, gdy jest wywoływana po raz pierwszy, a nie wcześniej. W powyższym przykładzie, który oznacza, że "`strGlobal`" ciągu nie będzie można skonstruować aż po raz pierwszy `SetGlobalString` lub `GetGlobalString` jest wywoływana. W niektórych przypadkach może to pomóc skrócić czas uruchamiania biblioteki DLL.

## <a name="thread-local-data"></a>Danych lokalnych wątku

Podobnie jak przetwarzanie danych lokalnych, danych lokalnych wątku służy dane muszą być lokalny dla danego wątku. Oznacza to potrzebne jest oddzielne wystąpienie danych dla każdego wątku, który uzyskuje dostęp do tych danych. Może to wiele razy służyć audytów mechanizmów rozbudowane synchronizacji. Jeśli dane nie musi być współużytkowane przez wiele wątków, takich mechanizmów może być kosztowne, a zbędne. Załóżmy, że Musieliśmy `CString` obiektu (podobne do powyższego przykładu). Możemy zwiększyć jej użyteczność wątku lokalnego opakowując go `CThreadLocal` szablonu:

```cpp
struct CMyThreadData : public CNoTrackObject
{
    CString strThread;
};
CThreadLocal<CMyThreadData> threadData;

void MakeRandomString()
{
    // a kind of card shuffle (not a great one)
    CString& str = threadData->strThread;
    str.Empty();
    while (str.GetLength() != 52)
    {
        unsigned int randomNumber;
        errno_t randErr;
        randErr = rand_s(&randomNumber);

        if (randErr == 0)
        {
            TCHAR ch = randomNumber % 52 + 1;
            if (str.Find(ch) <0)
            str += ch; // not found, add it
        }
    }
}
```

Jeśli `MakeRandomString` została wywołana z dwóch różnych wątków, każdy będzie "mieszania" ciągu na różne sposoby bez zakłócania drugiego. Jest to spowodowane jest faktycznie `strThread` wystąpienia na wątkiem, a nie tylko jedno wystąpienie globalne.

Należy zauważyć, jak odwołanie jest używane do przechwytywania `CString` adresów raz zamiast raz dla iteracji pętli. Kod pętli można została zapisana przy użyciu `threadData->strThread` wszędzie "`str`" jest używany, ale kod będzie znacznie wolniejsze podczas wykonywania. Najlepiej można buforować odwołanie do danych, gdy odwołania te występują w pętli.

`CThreadLocal` Szablonu klasy używa tych samych mechanizmów, `CProcessLocal` robi i te same techniki implementacji.

## <a name="see-also"></a>Zobacz także

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)
