---
title: 'TN058: Implementacja stanu modułu MFC | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.mfc.implementation
dev_langs:
- C++
helpviewer_keywords:
- thread state [MFC]
- module states [MFC], managing state data
- TN058
- MFC, managing state data
- module states [MFC], switching
- DLLs [MFC], module states
- process state [MFC]
ms.assetid: 72f5b36f-b3da-4009-a144-24258dcd2b2f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 90e407299f67922aa855a51b9983af074cdbd4fc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="tn058-mfc-module-state-implementation"></a>TN058: implementacja stanu modułu MFC
> [!NOTE]
>  Poniższe uwagi techniczne nie został zaktualizowany, ponieważ została ona uwzględniona w dokumentacji online. W związku z tym niektóre procedury i tematy mogą być nieaktualne lub niepoprawne. Najnowsze informacje zalecane jest, możesz wyszukać temat odsetek w indeksie dokumentacji online.  
  
 Ta uwaga techniczna opisuje implementacji konstrukcji "Stanu modułu MFC". Opis implementacja stanu modułu jest szczególnie ważne, za pomocą MFC współużytkowanych bibliotek DLL z biblioteki DLL (lub OLE w procesie serwera).  
  
 Przed przeczytaniem tej uwagi, odnoszą się do "Zarządzanie stanu danych z MFC — moduły" [tworzenie nowych dokumentów, okien i widoków](../mfc/creating-new-documents-windows-and-views.md). Ten artykuł zawiera informacje o użyciu ważne i ogólne informacje na ten temat.  
  
## <a name="overview"></a>Omówienie  
 Istnieją trzy rodzaje informacji o stanie MFC: stan modułu, stan procesu i stan wątku. Czasami można połączyć te typy stanu. Na przykład MFC dojścia mapy są zarówno moduł lokalnych, jak i lokalnego wątku. Dzięki temu dwóch różnych modułach mają różne mapy w każdym z ich wątków.  
  
 Stan procesu i stan wątku są podobne. Te elementy danych są rzeczy, które zostały tradycyjnie zmiennych globalnych, ale ma należy specyficzne dla danego procesu lub wątku obsługuje prawidłowego systemach Win32 lub właściwego Obsługa wielowątkowości. Element podanych danych mieści się w kategorii zależy od tego elementu i jego żądaną semantyki względem granic procesie i wątku.  
  
 Stan modułu jest unikatowa, w tym może zawierać naprawdę globalny stan lub stan procesu lokalnego lub lokalnej wątku. Ponadto go mogą być przełączane szybko.  
  
## <a name="module-state-switching"></a>Stan modułu przełączania  
 Każdy wątek zawiera wskaźnik do stanu "bieżący" lub "active" modułu (nie zaskakująco wskaźnika jest częścią lokalnej stan wątku MFC). Ten wskaźnik jest zmieniany, gdy wątek wykonywania przekazuje granicy modułu, takie jak aplikacja wywoływanie kontrolkę OLE lub biblioteki DLL lub formantu OLE wywołań zwrotnych do aplikacji.  
  
 Bieżący stan modułu jest włączane przez wywołanie metody **AfxSetModuleState**. W większości przypadków nigdy nie będzie uwzględniać bezpośrednio przy użyciu interfejsu API. MFC, w wielu przypadkach będzie wywoływać go dla Ciebie (w WinMain, wpis punktów OLE, **AfxWndProc**itp.). Jest to wykonywane w dowolny składnik zapisu łącząc statycznie w specjalny **WndProc**i specjalnego `WinMain` (lub `DllMain`) który zna stanu modułu, którego należy bieżący. Zostanie wyświetlony ten kod, analizując DLLMODUL. CPP lub APPMODUL. CPP w katalogu MFC\SRC.  
  
 Jest rzadko, czy chcesz ustawić stan modułu i nie jest ustawiony ponownie. W większości przypadków chcesz "push" własny moduł stanu jako bieżący i następnie, po zakończeniu "pop" ponownie oryginalnej kontekstu. Jest to realizowane przez makro [afx_manage_state —](reference/extension-dll-macros.md#afx_manage_state) i klasy specjalnej **AFX_MAINTAIN_STATE**.  
  
 `CCmdTarget` zawiera specjalne funkcje obsługi przełączenie stanu modułu. W szczególności `CCmdTarget` klasy głównym używana do automatyzacji OLE i OLE COM punktów wejścia. Inne punkty wejścia, takich jak połączenie z systemu, te punkty wejścia, należy ustawić stan prawidłowy moduł. Jak jest danego `CCmdTarget` wie, co stanie modułu "Popraw" powinno być odpowiedź jest czy go "pamięta" co "bieżący" Stan modułu jest, gdy jest on tworzony, tak, aby można go ustawić bieżący stan modułu, do którego "zapamiętanych" o nazwie wartość, gdy jest ona nowsza. W związku z tym moduł określają, że dany `CCmdTarget` obiekt jest skojarzony z jest w stanie modułu, które były aktualne, gdy obiekt został utworzony. Zająć prosty przykład ładowania serwera INPROC, tworzenia obiektu i wywołanie metody.  
  
1.  Biblioteki DLL ładowane przez OLE przy użyciu **LoadLibrary**.  
  
2. **RawDllMain** nazywa się najpierw. Ustawia stan modułu do stanu znane statycznych modułu dla biblioteki DLL. Z tego powodu **RawDllMain** połączone statycznie do pliku DLL.  
  
3.  Wywołania konstruktora fabryki klasy skojarzone z naszych obiektu. `COleObjectFactory` jest pochodną `CCmdTarget` i w związku z tym pamięta Państwa, w którym module wystąpienia. Jest to ważne — monit fabryki klasy do tworzenia obiektów zna teraz jakim stanie modułu, aby bieżący.  
  
4. `DllGetClassObject` nosi nazwę można uzyskać fabryki klasy. MFC wyszukuje na liście fabryki klasy skojarzone z tym modułem i zwraca go.  
  
5. **COleObjectFactory::XClassFactory2::CreateInstance** jest wywoływana. Przed utworzeniem obiektu i przywróceniem go, ta funkcja ustawia stan modułu do stanu modułu, które były aktualne w kroku 3 (jedną, która była bieżąca podczas `COleObjectFactory` wystąpienia). Jest to realizowane wewnątrz [method_prologue —](com-interface-entry-points.md).  
  
6.  Po utworzeniu obiektu zbyt jest `CCmdTarget` pochodnych i w ten sam sposób `COleObjectFactory` zapamiętanych stan modułu, który był aktywny, co powoduje to nowy obiekt. Teraz wie, których stan modułu, aby przełączyć się do obiektu zawsze, gdy jest wywoływana.  
  
7.  Klient wywołuje funkcję dla obiekt OLE COM, który otrzymał od jego `CoCreateInstance` wywołania. Gdy obiekt jest wywoływana używa `METHOD_PROLOGUE` Aby przełączyć stan modułu tak jak `COleObjectFactory` jest.  
  
 Jak widać, stan modułu są propagowane z obiektu do obiektu, ponieważ są one tworzone. Należy mieć ustawiony prawidłowo stan modułu. Jeśli nie jest ustawiona, obiekt biblioteki DLL lub COM może nieprawidłowo współpracować z aplikacji MFC, która powoduje wywołanie, może być nie można odnaleźć własnych zasobów lub może zakończyć się niepowodzeniem w inny sposób miserable.  
  
 Należy pamiętać, że niektóre rodzaje bibliotek DLL, w szczególności biblioteki dll "Rozszerzeń MFC" Przełącza stan modułu w ich **RawDllMain** (w rzeczywistości one zazwyczaj nie muszą nawet być **RawDllMain**). Jest to spowodowane są przeznaczone do zachowania "jak gdyby" obecny w aplikacji, która używa ich. Są znacznie część aplikacji, która działa i jest zamiar zmodyfikuj stan globalny tej aplikacji.  
  
 Formanty OLE i inne biblioteki DLL są bardzo różnią się. Nie chcą zmodyfikować stanu aplikacja wywołująca; Aplikacja, która je wywołuje nie można nawet aplikacji MFC i dlatego nie może istnieć bez stanu, aby zmodyfikować. Jest to powód, czy została opracowana przełączenie stanu modułu.  
  
 Dla funkcji wyeksportowanej z biblioteki DLL, który uruchamia okno dialogowe w bibliotece DLL należy dodać następujący kod na początku funkcji:  
  
```  
AFX_MANAGE_STATE(AfxGetStaticModuleState())  
```  
  
 Zamienia to bieżący stan modułu ze stanem zwrócony z [AfxGetStaticModuleState —](reference/extension-dll-macros.md#afxgetstaticmodulestate) do końca bieżącego zakresu.  
  
 Problemy z zasobami w bibliotekach DLL wystąpi, jeśli `AFX_MODULE_STATE` makro nie jest używany. Domyślnie MFC używa zasobów dojście aplikacji głównej do załadowania szablonu zasobów. Ten szablon faktycznie jest przechowywany w bibliotece DLL. Główną przyczyną jest informacji o stanie modułu MFC nie został przełączony przez `AFX_MODULE_STATE` makra. Dojście do zasobu jest odzyskiwana ze stanu modułu MFC. Nie przełączający stan modułu powoduje, że dojście niewłaściwego zasobu do użycia.  
  
 `AFX_MODULE_STATE` nie musi znajdować się w każdej funkcji w bibliotece DLL. Na przykład `InitInstance` może być wywoływany przez kod MFC w aplikacji bez `AFX_MODULE_STATE` ponieważ MFC automatycznie przenosi stan modułu przed `InitInstance` , a następnie przełącza ją tu później za `InitInstance` zwraca. Dotyczy to wszystkich programów obsługi mapy wiadomości. Regularne biblioteki DLL MFC faktycznie mają specjalne okna głównego procedury, która automatycznie zmienia stan modułu przed przesłaniem wiadomości.  
  
## <a name="process-local-data"></a>Dane lokalne procesu  
 Dane lokalne procesu nie będą takie nas bardzo ważne, gdyby nie został dla trudności modelu DLL systemach Win32. W systemach Win32 wszystkie biblioteki DLL udostępniać swoje dane globalne, nawet wtedy, gdy jest ładowany przez wiele aplikacji. Jest to bardzo różnią się od "rzeczywiste" modelu danych Win32 DLL, gdzie każdą bibliotekę DLL pobiera osobną kopię jego przestrzeni danych w każdym procesie, które dołącza do pliku DLL. Aby dodać do złożoności, danych przydzielone na stercie w systemach Win32 biblioteki DLL jest w rzeczywistości proces (przynajmniej w zakresie, ponieważ przechodzi własność). Należy wziąć pod uwagę następujące dane i kodu:  
  
```  
static CString strGlobal; // at file scope  
 
__declspec(dllexport)   
void SetGlobalString(LPCTSTR lpsz)  
{  
    strGlobal = lpsz;  
}  
 
__declspec(dllexport)  
void GetGlobalString(LPCTSTR lpsz,
    size_t cb)  
{  
    StringCbCopy(lpsz,
    cb,
    strGlobal);

}  
```  
  
 Należy rozważyć, co się stanie, jeśli kod powyżej w znajduje się w bibliotece DLL i ładowanie biblioteki DLL przez dwa procesy A i B (w rzeczywistości możliwe dwa wystąpienia tej samej aplikacji). Wywołania `SetGlobalString("Hello from A")`. W związku z tym jest przydzielana pamięć dla `CString` danych w ramach procesu A. zachować w pamiętać, że `CString` jest globalna i jest widoczny dla obu A i B. Teraz wywołuje B `GetGlobalString(sz, sizeof(sz))`. B będzie można wyświetlić dane, A ustawiona. Jest to spowodowane systemach Win32 oferuje Brak ochrony między procesy, takie jak jest Win32. To pierwszy problemu. w wielu przypadkach nie jest pożądane, aby jednej aplikacji wpływa na dane globalne, który jest uważany za należeć do innej aplikacji.  
  
 Istnieją również dodatkowe problemy. Załóżmy, że teraz kończy pracę. Po zamknięciu A, pamięci używanej przez "`strGlobal`" ciąg ma zostać udostępnione dla systemu — to znaczy wszystkich pamięci przydzielonej przez proces A jest zwalniane automatycznie przez system operacyjny. Nie zostanie zwolniona, ponieważ `CString` destruktora jest wywoływana; nie została wywołana jeszcze. Zostanie zwolniona po prostu ponieważ aplikacji, w której przydzielony opuścił sceny. Teraz, gdy wywołana B `GetGlobalString(sz, sizeof(sz))`, nie może on uzyskać prawidłowe dane. Inna aplikacja może użyć pamięci, do czegoś innego.  
  
 Wyraźnie istnieje problem. MFC 3.x używana jest metoda zwana lokalny magazyn wątków (TLS). MFC 3.x czy przydzielić indeks TLS działającego w systemach Win32 naprawdę jako indeks proces lokalny magazyn, nawet jeśli nie jest wywoływany który, a następnie będzie odwołania wszystkich danych w oparciu o ten indeks TLS. Jest to podobne do indeksu TLS, który został użyty do przechowywania danych lokalnych wątku na Win32 (Aby uzyskać więcej informacji na ten temat zobacz poniżej). Przyczyną co biblioteki MFC DLL mogą korzystać z co najmniej dwóch wskaźników TLS na proces. Podczas ładowania wielu OLE kontroli biblioteki dll (formanty ocx) zostało uwzględnione, szybko uruchomić poza indeksów TLS (Brak dostępnych tylko 64). Ponadto MFC było umieścić te dane w jednym miejscu, struktura single. Nie można rozszerzyć bardzo, a nie nadaje się doskonale względem jego użycie indeksów TLS.  
  
 MFC 4.x rozwiązuje ten problem z zestawem szablonów klas można "zawijać" wokół danych, który powinien być lokalny proces. Na przykład wymienione powyżej może być problemu pisząc:  
  
```  
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
  
 MFC implementuje to w dwóch krokach. Najpierw jest warstwą Win32 **Tls\***  interfejsów API (**TlsAlloc**, **TlsSetValue**, **TlsGetValue**, itd.) który tylko dwa indeksów TLS na proces, niezależnie od tego, jak wiele bibliotek DLL należy użyć. Drugi, `CProcessLocal` szablonu mają dostęp do tych danych. Zastępuje on operator ->, czyli, co umożliwia intuicyjne składni, zobacz powyżej. Wszystkie obiekty, które są kodowane przez `CProcessLocal` musi pochodzić z `CNoTrackObject`. `CNoTrackObject` udostępnia alokatora niższego poziomu (**Funkcja LocalAlloc**/**LocalFree**) i destruktor wirtualny tak, aby MFC automatycznie można zniszczyć lokalnych obiektów procesu, gdy proces jest zakończony. Takie obiekty mogą mieć niestandardowe — destruktor, jeśli wymagane jest dodatkowe oczyszczanie. Powyższy przykład nie wymaga jednego, ponieważ kompilator wygeneruje destruktora domyślne można zniszczyć osadzonego `CString` obiektu.  
  
 Istnieją inne ciekawe zalety tej metody. Są nie tylko wszystkie `CProcessLocal` obiektów zniszczone automatycznie, nie są skonstruować dopóki nie są potrzebne. `CProcessLocal::operator->` zostanie utworzenie wystąpienia skojarzonego obiektu jest ona wywoływana po raz pierwszy, a nie wcześniej. W powyższym przykładzie oznacza to, że "`strGlobal`" ciągu nie będzie można skonstruować dopiero po raz pierwszy **SetGlobalString** lub **GetGlobalString** jest wywoływana. W niektórych przypadkach może to pomóc zmniejszyć czas uruchamiania biblioteki DLL.  
  
## <a name="thread-local-data"></a>Dane lokalne wątków  
 Podobne do przetwarzania danych lokalnych danych lokalnych wątku służy dane muszą być lokalne dla danego wątku. Oznacza to, że należy oddzielnego wystąpienia dane dla każdego wątku, który uzyskuje dostęp do tych danych. To wielokrotnie można zamiast mechanizmów szeroką gamę synchronizacji. Jeśli dane nie musi być współużytkowane przez wiele wątków, takich mechanizmów może być kosztowne i niepotrzebne. Załóżmy, że było `CString` obiektu (podobne jak w przypadku powyższego przykładu). Firma Microsoft może ułatwić wątków lokalnych, opakowując go przy użyciu `CThreadLocal` szablonu:  
  
```  
struct CMyThreadData : public CNoTrackObject  
{  
    CString strThread;  
};  
CThreadLocal<CMyThreadData> threadData;  
 
void MakeRandomString()  
{ *// a kind of card shuffle (not a great one)  
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
  
 Jeśli `MakeRandomString` została wywołana z dwóch różnych wątkach, każda będzie "losowo" ciąg na różne sposoby bez zakłócania innych. Ponieważ jest rzeczywiście `strThread` wystąpienia na wątkiem, a nie tylko jedno wystąpienie globalnego.  
  
 Należy zwrócić uwagę, jak odwołanie służy do przechwytywania `CString` adresów raz zamiast raz na iteracji pętli. Kod pętli można zapisać z `threadData->strThread` wszędzie "`str`" jest używana, ale kod będzie znacznie mniejsza podczas wykonywania. Najlepiej pamięci podręcznej odwołanie do danych w przypadku wystąpienia takich odwołań w pętli.  
  
 `CThreadLocal` Szablonu klasy używane te same mechanizmy który `CProcessLocal` ma i te same techniki implementacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)   
 [Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)

