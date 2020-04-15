---
title: 'TN058: implementacja stanu modułu MFC'
ms.date: 06/28/2018
helpviewer_keywords:
- thread state [MFC]
- module states [MFC], managing state data
- TN058
- MFC, managing state data
- module states [MFC], switching
- DLLs [MFC], module states
- process state [MFC]
ms.assetid: 72f5b36f-b3da-4009-a144-24258dcd2b2f
ms.openlocfilehash: b64fb6b97474007c44a2124315e83e1ac119f9ec
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366608"
---
# <a name="tn058-mfc-module-state-implementation"></a>TN058: implementacja stanu modułu MFC

> [!NOTE]
> Następująca uwaga techniczna nie została zaktualizowana, ponieważ została po raz pierwszy uwzględniona w dokumentacji online. W rezultacie niektóre procedury i tematy mogą być nieaktualne lub nieprawidłowe. Aby uzyskać najnowsze informacje, zaleca się wyszukicie tematu interesującego w indeksie dokumentacji online.

W tej notatce technicznej opisano implementację konstrukcji "stan modułu" MFC. Zrozumienie implementacji stanu modułu ma kluczowe znaczenie dla korzystania z bibliotek DLL udostępnionych MFC z bibliotek DLL (lub ole w procesie serwera).

Przed przeczytaniem tej notatki zapoznaj się z "Zarządzanie danymi o stanie modułów MFC" w [temacie Tworzenie nowych dokumentów, systemu Windows i widoków](../mfc/creating-new-documents-windows-and-views.md). Ten artykuł zawiera ważne informacje o użyciu i informacje ogólne na ten temat.

## <a name="overview"></a>Omówienie

Istnieją trzy rodzaje informacji o stanie MFC: stan modułu, stan procesu i stan wątku. Czasami te typy stanu można łączyć. Na przykład mapy dojścia MFC są zarówno lokalne modułu, jak i lokalne wątki. Dzięki temu dwa różne moduły mają różne mapy w każdym z ich wątków.

Stan procesu i stan wątku są podobne. Te elementy danych są rzeczy, które tradycyjnie były zmienne globalne, ale muszą być specyficzne dla danego procesu lub wątku dla prawidłowej obsługi Win32s lub dla prawidłowej obsługi wielowątkowej. Kategoria, do której pasuje dany element danych, zależy od tego elementu i jego pożądanej semantyki w odniesieniu do granic procesu i wątku.

Stan modułu jest unikatowy, ponieważ może zawierać prawdziwie globalny stan lub stan, który jest procesem lokalnym lub lokalnym wątku. Ponadto można go szybko przełączyć.

## <a name="module-state-switching"></a>Przełączanie stanu modułu

Każdy wątek zawiera wskaźnik do stanu modułu "current" lub "active" (nic dziwnego, że wskaźnik jest częścią lokalnego stanu wątku MFC). Ten wskaźnik jest zmieniany, gdy wątek wykonywania przechodzi granicy modułu, takich jak aplikacja wywołująca do kontroli OLE lub biblioteki DLL lub kontroli OLE wywołanie z powrotem do aplikacji.

Bieżący stan modułu jest `AfxSetModuleState`przełączany przez wywołanie . W przeważającej części nigdy nie będzie zajmować się bezpośrednio z interfejsem API. MFC, w wielu przypadkach, będzie go nazywać dla Ciebie (w WinMain, OLE entry-pointy, `AfxWndProc`itp.). Odbywa się to w każdym składniku, który `WndProc`piszesz statycznie łącząc w specjalnym , i specjalny `WinMain` (lub `DllMain`), który wie, który stan modułu powinien być aktualny. Możesz zobaczyć ten kod, patrząc na DLLMODUL. CPP lub APPMODUL. CPP w katalogu MFC\SRC.

Rzadko zdarza się, że chcesz ustawić stan modułu, a następnie nie ustawić go z powrotem. W większości przypadków chcesz "wypchnąć" własny stan modułu jako bieżący, a następnie, po zakończeniu, "pop" oryginalny kontekst z powrotem. Odbywa się to za pomocą [AFX_MANAGE_STATE](reference/extension-dll-macros.md#afx_manage_state) makro `AFX_MAINTAIN_STATE`i klasy specjalnej .

`CCmdTarget`posiada specjalne funkcje wspomagające przełączanie stanu modułu. W szczególności `CCmdTarget` jest klasą główną używaną dla automatyzacji OLE i punktów wejścia OLE COM. Podobnie jak każdy inny punkt wejścia narażony na system, te punkty wejścia muszą ustawić prawidłowy stan modułu. Skąd dany `CCmdTarget` wie, jaki powinien być "poprawny" stan modułu Odpowiedź jest taka, że "pamięta", jaki jest stan modułu "current", gdy jest konstruowany, tak aby można było ustawić bieżący stan modułu na tę wartość "zapamiętaną", gdy jest później wywoływana. W rezultacie stan modułu, `CCmdTarget` z którym jest skojarzony dany obiekt, jest stanem modułu, który był aktualny podczas konstruowania obiektu. Weźmy prosty przykład ładowania serwera INPROC, tworzenia obiektu i wywoływania jego metod.

1. Biblioteka DLL jest `LoadLibrary`ładowana przez ole przy użyciu .

1. `RawDllMain`nazywa się pierwszy. Ustawia stan modułu na znany stan modułu statycznego dla biblioteki DLL. Z tego `RawDllMain` powodu jest statycznie związane z biblioteką DLL.

1. Konstruktor fabryki klasy skojarzone z naszym obiektem jest wywoływana. `COleObjectFactory`pochodzi z `CCmdTarget` i w rezultacie pamięta, w jakim stanie modułu został szebrany. Jest to ważne — gdy fabryka klas jest proszona o utworzenie obiektów, wie teraz, jaki stan modułu ma być aktualny.

1. `DllGetClassObject`jest wywoływana w celu uzyskania fabryki klasy. MFC przeszukuje listę fabryczną klas skojarzoną z tym modułem i zwraca ją.

1. `COleObjectFactory::XClassFactory2::CreateInstance`nazywa się. Przed utworzeniem obiektu i zwróceniem go, ta funkcja ustawia stan modułu do stanu modułu, który `COleObjectFactory` był bieżący w kroku 3 (ten, który był aktualny, gdy został sygnowany). Odbywa się to wewnątrz [METHOD_PROLOGUE](com-interface-entry-points.md).

1. Po utworzeniu obiektu również jest `CCmdTarget` pochodną i `COleObjectFactory` w ten sam sposób zapamiętany, który stan modułu był aktywny, podobnie jak ten nowy obiekt. Teraz obiekt wie, do którego stanu modułu przełączyć się za każdym razem, gdy jest wywoływana.

1. Klient wywołuje funkcję na obiektu OLE COM, który otrzymał od swojego `CoCreateInstance` wywołania. Gdy obiekt jest wywoływany `METHOD_PROLOGUE` używa do przełączania `COleObjectFactory` stanu modułu, podobnie jak robi.

Jak widać, stan modułu jest propagowany z obiektu do obiektu, ponieważ są one tworzone. Ważne jest, aby stan modułu był odpowiednio ustawiony. Jeśli nie jest ustawiona, dll lub obiekt COM może wchodzić w interakcje słabo z aplikacją MFC, która wywołuje go lub może nie być w stanie znaleźć własne zasoby lub może zakończyć się niepowodzeniem w inny nieszczęśliwy sposób.

Należy pamiętać, że niektóre rodzaje bibliotek DLL, w szczególności "MFC Extension" `RawDllMain` bibliotek dll nie przełączają `RawDllMain`stan modułu w ich (w rzeczywistości, zwykle nawet nie mają ). To dlatego, że są one przeznaczone do zachowania "tak, jakby" były one rzeczywiście obecne w aplikacji, która ich używa. Są one bardzo częścią aplikacji, która jest uruchomiona i jest ich zamiarem, aby zmodyfikować stan globalny tej aplikacji.

Kontrolki OLE i inne biblioteki DLL są bardzo różne. Nie chcą modyfikować stanu aplikacji wywołującej; aplikacja, która wywołuje je może nawet nie być aplikacją MFC i dlatego może być żaden stan do zmodyfikowania. Z tego powodu wynaleziono przełączanie stanu modułu.

W przypadku eksportowanych funkcji z biblioteki DLL, takich jak ta, która uruchamia okno dialogowe w dll, należy dodać następujący kod na początku funkcji:

```cpp
AFX_MANAGE_STATE(AfxGetStaticModuleState())
```

Spowoduje to zamianę bieżącego stanu modułu ze stanem zwróconym z [AfxGetStaticModuleState](reference/extension-dll-macros.md#afxgetstaticmodulestate) do końca bieżącego zakresu.

Jeśli AFX_MODULE_STATE makro nie jest używane, wystąpią problemy z zasobami bibliotek DLL. Domyślnie MFC używa dojścia zasobów aplikacji głównej do załadowania szablonu zasobu. Ten szablon jest faktycznie przechowywany w dll. Główną przyczyną jest to, że informacje o stanie modułu MFC nie zostały przełączone przez makro AFX_MODULE_STATE. Dojście zasobów jest odzyskiwane ze stanu modułu MFC. Nie przełączanie stanu modułu powoduje, że niewłaściwy dojście do zasobu ma być używany.

AFX_MODULE_STATE nie musi być umieszczana w każdej funkcji w dll. Na przykład `InitInstance` może być wywoływana przez kod MFC w aplikacji bez AFX_MODULE_STATE ponieważ MFC `InitInstance` automatycznie przesuwa stan `InitInstance` modułu przed, a następnie przełącza go z powrotem po zwraca. To samo dotyczy wszystkich programów obsługi map wiadomości. Zwykłe biblioteki DLL MFC faktycznie mają specjalną procedurę okna głównego, która automatycznie przełącza stan modułu przed przekierowaniem dowolnego komunikatu.

## <a name="process-local-data"></a>Przetwarzanie danych lokalnych

Przetwarzanie danych lokalnych nie byłoby tak wielkim problemem, gdyby nie trudność modelu DLL Win32s. W win32s wszystkie biblioteki DLL współużytkują swoje dane globalne, nawet po załadowaniu przez wiele aplikacji. To bardzo różni się od "rzeczywistego" modelu danych DLL Win32, gdzie każda biblioteka DLL pobiera oddzielną kopię miejsca na dane w każdym procesie, który jest dołączony do biblioteki DLL. Aby dodać do złożoności, dane przydzielone na stercie w win32s DLL jest w rzeczywistości proces specyficzne (co najmniej w miarę własności idzie). Należy wziąć pod uwagę następujące dane i kod:

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

Należy wziąć pod uwagę, co się stanie, jeśli powyższy kod znajduje się w dll i że biblioteka DLL jest ładowany przez dwa procesy A i B (w rzeczywistości może to być dwa wystąpienia tej samej aplikacji). Połączenia `SetGlobalString("Hello from A")`. W rezultacie pamięć jest przydzielana dla `CString` danych w kontekście procesu `CString` A. Należy pamiętać, że sama jest globalna i jest widoczna zarówno dla A, jak i B. Teraz B `GetGlobalString(sz, sizeof(sz))`wzywa . B będzie mógł zobaczyć dane ustawione przez A. To dlatego, że Win32s oferuje żadnej ochrony między procesami, takich jak Win32 nie. To jest pierwszy problem; w wielu przypadkach nie jest pożądane, aby jedna aplikacja wpływała na dane globalne, które są uważane za należące do innej aplikacji.

Istnieją również dodatkowe problemy. Powiedzmy, że A teraz wychodzi. Po zamknięciu A pamięć używana`strGlobal`przez ciąg ' jest dostępna dla systemu — oznacza to, że cała pamięć przydzielona przez proces A jest zwalniana automatycznie przez system operacyjny. Nie jest zwalniany, `CString` ponieważ destruktor jest wywoływany; nie został jeszcze powołany. Jest zwalniany tylko dlatego, że aplikacja, która została przydzielona opuścił scenę. Teraz, jeśli `GetGlobalString(sz, sizeof(sz))`B wywołane , może nie uzyskać prawidłowe dane. Niektóre inne aplikacje mogą mieć używane tej pamięci dla czegoś innego.

Oczywiście istnieje problem. MFC 3.x używane techniki o nazwie thread-local storage (TLS). MFC 3.x przydzieli indeks TLS, który w obszarze Win32s naprawdę działa jako indeks magazynu lokalnego procesu, nawet jeśli nie jest wywoływana, a następnie odwołuje się do wszystkich danych na podstawie tego indeksu TLS. Jest to podobne do indeksu TLS, który był używany do przechowywania danych lokalnych wątków w win32 (zobacz poniżej, aby uzyskać więcej informacji na ten temat). Spowodowało to, że każda biblioteka DLL MFC wykorzystywała co najmniej dwa indeksy TLS na proces. Podczas ładowania wielu bibliotek DLL kontroli OLE (OCXs) szybko zabraknie indeksów TLS (dostępnych jest tylko 64). Ponadto MFC musiał umieścić wszystkie te dane w jednym miejscu, w jednej strukturze. Nie był zbyt rozszerzalny i nie był idealny w odniesieniu do stosowania indeksów TLS.

MFC 4.x rozwiązuje ten problem za pomocą zestawu szablonów klas, które można "zawinąć" wokół danych, które powinny być lokalne. Na przykład problem, o którym mowa powyżej, można rozwiązać pisząc:

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

MFC implementuje to w dwóch etapach. Po pierwsze, istnieje warstwa na górze Interfejsów API __Tls\* __ Win32 **(TlsAlloc**, **TlsSetValue**, **TlsGetValue**, itp.), które używają tylko dwa indeksy TLS na proces, bez względu na to, ile bibliotek DLL masz. Po drugie, szablon jest dostarczany, `CProcessLocal` aby uzyskać dostęp do tych danych. Zastępuje operator-> co pozwala intuicyjnej składni, którą widzisz powyżej. Wszystkie obiekty, które `CProcessLocal` są zawijane przez muszą pochodzić z `CNoTrackObject`. `CNoTrackObject`zapewnia alokator niższego poziomu **(LocalAlloc**/**LocalFree)** i wirtualny destruktor, dzięki czemu MFC może automatycznie zniszczyć lokalne obiekty procesu po zakończeniu procesu. Takie obiekty mogą mieć niestandardowy destruktor, jeśli wymagane jest dodatkowe oczyszczanie. Powyższy przykład nie wymaga jednego, ponieważ kompilator wygeneruje domyślny `CString` destruktor, aby zniszczyć obiekt osadzony.

Istnieją inne interesujące zalety tego podejścia. Nie tylko `CProcessLocal` wszystkie obiekty są niszczone automatycznie, nie są one konstruowane, dopóki nie są potrzebne. `CProcessLocal::operator->`spowoduje wystąpienie skojarzonego obiektu przy pierwszym wywołaniu i nie wcześniej. W powyższym przykładzie oznacza`strGlobal`to, że ciąg ' nie `SetGlobalString` zostanie `GetGlobalString` skonstruowany do pierwszego razu lub zostanie wywołany. W niektórych przypadkach może to pomóc zmniejszyć czas uruchamiania biblioteki DLL.

## <a name="thread-local-data"></a>Dane lokalne wątku

Podobnie jak w przypadku przetwarzania danych lokalnych, dane lokalne wątku jest używany, gdy dane muszą być lokalne do danego wątku. Oznacza to, że potrzebujesz osobnego wystąpienia danych dla każdego wątku, który uzyskuje dostęp do tych danych. Może to być wielokrotnie używane zamiast rozległych mechanizmów synchronizacji. Jeśli dane nie muszą być współużytkowane przez wiele wątków, takie mechanizmy mogą być kosztowne i niepotrzebne. Załóżmy, `CString` że mieliśmy obiekt (podobnie jak w powyższej próbce). Możemy zrobić to wątku lokalnego, owijając go z szablonem: `CThreadLocal`

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

Jeśli `MakeRandomString` został wywołany z dwóch różnych wątków, każdy będzie "shuffle" ciąg na różne sposoby bez zakłócania innych. Dzieje się tak, `strThread` ponieważ w rzeczywistości istnieje wystąpienie na wątek, a nie tylko jedno wystąpienie globalne.

Należy zauważyć, jak odwołanie `CString` jest używany do przechwytywania adres raz zamiast raz na iteracji pętli. Kod pętli może być napisany `threadData->strThread` z`str`wszędzie ' ' jest używany, ale kod będzie znacznie wolniej w wykonaniu. Najlepiej jest buforować odwołanie do danych, gdy takie odwołania występują w pętlach.

Szablon `CThreadLocal` klasy używa tych samych mechanizmów, które `CProcessLocal` nie i te same techniki implementacji.

## <a name="see-also"></a>Zobacz też

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)
