---
title: Formant aplikacji | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.mfc.macros
dev_langs: C++
helpviewer_keywords: application control [MFC]
ms.assetid: c1f69f15-e0fe-4515-9f36-d63d31869deb
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c055f5489c7b85f5f974256709451426b614db47
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="application-control"></a>Sterowanie aplikacjami
OLE wymaga znacznej kontrolę nad ich obiektów i aplikacji. Biblioteki DLL systemu OLE musi mieć możliwość uruchamiania i automatycznie wersji aplikacji, koordynować ich produkcyjnego i modyfikacji obiektów i tak dalej. Funkcje, w tym temacie spełnienia tych wymagań. Oprócz wywoływana przez system OLE bibliotek DLL, można wywołać przez aplikacje, a także czasami tych funkcji. 
  
### <a name="application-control"></a>Sterowanie aplikacjami  
  
|||  
|-|-|  
|[Afxolecanexitapp —](#afxolecanexitapp)|Wskazuje, czy aplikacja może obsłużyć.|  
|[Afxolegetmessagefilter —](#afxolegetmessagefilter)|Pobiera bieżący filtr komunikatów aplikacji.|  
|[Afxolegetuserctrl —](#afxolegetuserctrl)|Pobiera bieżący flagi kontrolki użytkownika.|  
|[Afxolesetuserctrl —](#afxolesetuserctrl)|Ustawia lub usuwa flagę kontrolki użytkownika.|  
|[AfxOleLockApp](#afxolelockapp)|Zwiększa liczbę globalne w ramach liczby obiektów aktywnych w aplikacji.|  
|[Afxolelockcontrol —](#afxolelockcontrol)| Blokuje fabryki klasy określonego formantu. |
|[AfxOleUnlockApp](#afxoleunlockapp)|Zmniejsza framework liczba obiektów aktywnych w aplikacji.| 
|[Afxoleunlockcontrol —](#afxoleunlockcontrol)| Umożliwia odblokowanie fabryki klasy określonego formantu. |
|[Afxoleregisterserverclass —](#afxoleregisterserverclass)|Rejestruje serwer w rejestrze systemu OLE.|  
|[Afxoleseteditmenu —](#afxoleseteditmenu)|Implementuje interfejs użytkownika dla *typename* obiekt polecenia.|  

  
##  <a name="afxolecanexitapp"></a>Afxolecanexitapp —  
 Wskazuje, czy aplikacja może obsłużyć.  
  
```   
BOOL AFXAPI AfxOleCanExitApp(); 
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli aplikacja może wyjść; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Aplikacja nie powinna przerywane, jeśli istnieją oczekujących odwołań do jej obiektów. Funkcje globalne `AfxOleLockApp` i `AfxOleUnlockApp` zwiększyć i zmniejszyć odpowiednio licznikiem odwołań do obiektów w aplikacji. Aplikacja należy nie wygasa, gdy ten licznik jest różna od zera. Jeśli licznik jest różna od zera, głównego okna aplikacji jest ukryty (nie niszczone), gdy użytkownik wybierze Zamknij z menu systemowego lub zakończenia w menu Plik. Struktura wywołuje tej funkcji **CFrameWnd::OnClose**.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCAutomation#2](../../mfc/codesnippet/cpp/application-control_1.cpp)]  

## <a name="requirements"></a>Wymagania  
 **Nagłówek**: afxdisp.h 

##  <a name="afxolegetmessagefilter"></a>Afxolegetmessagefilter —  
 Pobiera bieżący filtr komunikatów aplikacji.  
  
```   
COleMessageFilter* AFXAPI AfxOleGetMessageFilter(); 
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do bieżącego filtra wiadomości.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji można uzyskać dostępu do bieżącego `COleMessageFilter`-pochodnych obiektu, tak samo, jak możesz wywołać `AfxGetApp` dostępu do bieżącego obiektu aplikacji.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCAutomation#3](../../mfc/codesnippet/cpp/application-control_2.cpp)]  
  
 [!code-cpp[NVC_MFCAutomation#4](../../mfc/codesnippet/cpp/application-control_3.cpp)]  

### <a name="requirements"></a>Wymagania  
 **Nagłówek**: afxwin.h 

##  <a name="afxolegetuserctrl"></a>Afxolegetuserctrl —  
 Pobiera bieżący flagi kontrolki użytkownika.  
  
```   
BOOL AFXAPI AfxOleGetUserCtrl(); 
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli użytkownik jest w formancie aplikacji; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Użytkownik jest w formancie aplikacji, gdy użytkownik ma jawnie otworzyć lub utworzyć nowy dokument. Użytkownik jest również w formancie Jeśli aplikacja nie została uruchomiona w systemie OLE biblioteki DLL — innymi słowy, jeśli użytkownik uruchomił aplikację z powłoką systemu.  

### <a name="requirements"></a>Wymagania  
 **Nagłówek**: afxdisp.h

##  <a name="afxolesetuserctrl"></a>Afxolesetuserctrl —  
 Ustawia lub usuwa flagę kontrolki użytkownika, które wyjaśniono w odwołaniu do `AfxOleGetUserCtrl`.  
  
```  
void AFXAPI AfxOleSetUserCtrl(BOOL bUserCtrl); 
```  
  
### <a name="parameters"></a>Parametry  
 *bUserCtrl*  
 Określa, czy można ustawić lub wyczyścić flagę kontrolki użytkownika.  
  
### <a name="remarks"></a>Uwagi  
 Struktura wywołuje tej funkcji, gdy użytkownik tworzy i ładuje dokumentu, ale nie podczas ładowania dokumentu lub została utworzona za pośrednictwem pośrednie akcja, taka jak ładowania osadzonego obiektu z aplikacji kontenera.  
  
 Wywołanie tej funkcji, jeśli inne akcje w aplikacji należy umieścić użytkownika w formancie aplikacji.  

### <a name="requirements"></a>Wymagania  
 **Nagłówek**: afxdisp.h

##  <a name="afxolelockapp"></a>AfxOleLockApp  
 Zwiększa liczbę globalne w ramach liczby obiektów aktywnych w aplikacji.  
  
```   
void AFXAPI AfxOleLockApp(); 
```  
  
### <a name="remarks"></a>Uwagi  
 Platformę śledzi liczbę liczbę obiektów active w aplikacji. `AfxOleLockApp` i `AfxOleUnlockApp` funkcji, odpowiednio zwiększyć i zmniejszyć tej liczby.  
  
 Gdy użytkownik próbuje zamknąć aplikację, która ma aktywne obiekty — aplikacja, dla którego jest różna od zera, liczba obiektów usługi active — platformę ukrywa aplikacji z punktu widzenia użytkownika zamiast całkowicie zamykania. `AfxOleCanExitApp` Funkcji wskazuje, czy aplikacja może obsłużyć.  
  
 Wywołanie `AfxOleLockApp` z dowolnych obiektów, która udostępnia interfejsy OLE, jeśli będzie niepożądanych dla tego obiektu, które mają zostać zniszczone, gdy nadal jest używana przez aplikację klienta. Także wywołać `AfxOleUnlockApp` w destruktorze dowolnego obiektu, który wywołuje `AfxOleLockApp` w konstruktorze. Domyślnie `COleDocument` (i klasy pochodne) automatycznie blokowania i odblokowywania aplikacji.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCAutomation#5](../../mfc/codesnippet/cpp/application-control_4.cpp)]  

### <a name="requirements"></a>Wymagania  
 **Nagłówek**: afxdisp.h

##  <a name="afxoleunlockapp"></a>AfxOleUnlockApp  
 Zmniejsza framework liczba obiektów aktywnych w aplikacji.  
  
```   
void AFXAPI AfxOleUnlockApp(); 
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz `AfxOleLockApp` Aby uzyskać więcej informacji.  
  
 Gdy liczba obiektów active osiągnie wartość 0, **AfxOleOnReleaseAllObjects** jest wywoływana.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [AfxOleLockApp](#afxolelockapp).  

### <a name="requirements"></a>Wymagania  
 **Nagłówek**: afxdisp.h  

 ## <a name="afxolelockcontrol"></a>AfxOleLockControl
Blokuje fabryki klasy określonego formantu danych dynamicznie utworzony, skojarzony z formantem pozostaje w pamięci.  
   
### <a name="syntax"></a>Składnia    
```
BOOL AFXAPI AfxOleLockControl(  REFCLSID clsid  );  
BOOL AFXAPI AfxOleLockControl( LPCTSTR lpszProgID );  
```
### <a name="parameters"></a>Parametry  
 `clsid`  
 Identyfikator unikatowy klasy formantu.  
  
 `lpszProgID`  
 Unikatowy identyfikator formantu.  
   
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli fabryka klas formantu zostało pomyślnie zablokowane; w przeciwnym razie 0.  
   
### <a name="remarks"></a>Uwagi  
 To znacznie przyspieszyć wyświetlania kontrolki. Na przykład po Tworzenie formantu w oknie dialogowym i przy zablokować kontrolki z `AfxOleLockControl`, nie trzeba tworzyć i zamknij go ponownie za każdym razem, gdy okno dialogowe jest wyświetlane lub zniszczenia. Jeśli użytkownik otwiera i zamyka okno dialogowe wielokrotnie, blokowanie formantów może znacznie poprawić wydajność. Gdy wszystko będzie gotowe do zniszczenia kontrolki wywołania `AfxOleUnlockControl`.  
   
### <a name="example"></a>Przykład  
```cpp
// Starts and locks control's (Microsoft Calendar) class factory. 
// Control will remain in memory for lifetime of
// application or until AfxOleUnlockControl() is called.

AfxOleLockControl(_T("MSCAL.Calendar"));
```
   
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** < afxwin.h >  
   
### <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne](mfc-macros-and-globals.md)   
 [Afxoleunlockcontrol —](#afxoleunlockcontrol)
 
##  <a name="afxoleregisterserverclass"></a>Afxoleregisterserverclass —  
 Dzięki tej funkcji, należy zarejestrować serwer w rejestrze systemu OLE.  
  
```   
BOOL AFXAPI AfxOleRegisterServerClass(
    REFCLSID clsid,  
    LPCTSTR lpszClassName,  
    LPCTSTR lpszShortTypeName,  
    LPCTSTR lpszLongTypeName,  
    OLE_APPTYPE nAppType = OAT_SERVER,  
    LPCTSTR* rglpszRegister = NULL,  
    LPCTSTR* rglpszOverwrite = NULL); 
```  
  
### <a name="parameters"></a>Parametry  
 `clsid`  
 Odwołanie do identyfikatora klasy OLE serwera  
  
 `lpszClassName`  
 Wskaźnik do ciągu zawierającego nazwę klasy obiektów serwera.  
  
 *lpszShortTypeName*  
 Wskaźnik do ciągu zawierającego krótką nazwę serwera typu obiektu, takiego jak "Wykresu".  
  
 *lpszLongTypeName*  
 Wskaźnik do ciąg zawierający długa nazwa typu obiektu serwera, na przykład "Wykres programu Microsoft Excel w wersji 5.0".  
  
 `nAppType`  
 Wartość, z **OLE_APPTYPE** wyliczenie określenie typu aplikacji OLE. Możliwe wartości są następujące:  
  
- `OAT_INPLACE_SERVER`Serwer ma interfejs użytkownika całego serwera.  
  
- `OAT_SERVER`Serwer obsługuje tylko osadzania.  
  
- `OAT_CONTAINER`Kontener obsługuje łącza do osadzonego.  
  
- `OAT_DISPATCH_OBJECT``IDispatch`-stanie obiektu.  
  
 `rglpszRegister`  
 Tablicy wskaźników do ciągów reprezentujących klucze i wartości, które mają zostać dodane do rejestru systemowego OLE, jeśli zostaną znalezione nie istniejące wartości kluczy.  
  
 `rglpszOverwrite`  
 Tablicy wskaźników do ciągów reprezentujących klucze i wartości do dodania do rejestru systemowego OLE Rejestr zawiera istniejące wartości dla danych kluczy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli klasa serwera zostanie pomyślnie zarejestrowana; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Większość aplikacji można użyć **COleTemplateServer::Register** zarejestrować typy dokumentów aplikacji. Jeśli format rejestru systemowego aplikacji nie mieści się typowy wzorzec, możesz użyć `AfxOleRegisterServerClass` uzyskać większą kontrolę.  
  
 Rejestr zawiera zestaw kluczy i wartości. `rglpszRegister` i `rglpszOverwrite` argumenty są tablic wskaźników do ciągów, składające się z klucza i wartości rozdzielonych **NULL** znak ( `'\0'`). Każdy z tych ciągów może mieć parametry wymienne, którego miejsca są oznaczane sekwencje znaków `%1` za pośrednictwem `%5`.  
  
 Symbole są wypełnione następujący sposób:  
  
|Symbol|Wartość|  
|------------|-----------|  
|%1|Identyfikator klasy, w formacie ciągu|  
|%2|Nazwa klasy|  
|%3|Ścieżka do pliku wykonywalnego|  
|%4|Wpisz krótką nazwę|  
|%5|Nazwa typu Long|  

### <a name="requirements"></a>Wymagania  
 **Nagłówek**: afxdisp.h

##  <a name="afxoleseteditmenu"></a>Afxoleseteditmenu —  
 Implementuje interfejs użytkownika dla *typename* obiekt polecenia.  
  
```   
void AFXAPI AfxOleSetEditMenu(
    COleClientItem* pClient,  
    CMenu* pMenu,  
    UINT iMenuItem,  
    UINT nIDVerbMin,  
    UINT nIDVerbMax = 0,  
    UINT nIDConvert = 0); 
```  
  
### <a name="parameters"></a>Parametry  
 `pClient`  
 Wskaźnik do elementu OLE klienta.  
  
 `pMenu`  
 Wskaźnik do obiektu menu aktualizacji.  
  
 *iMenuItem*  
 Indeks elementu menu aktualizacji.  
  
 `nIDVerbMin`  
 Identyfikator polecenia umożliwiająca zlecenia głównego.  
  
 *nIDVerbMax*  
 Identyfikator polecenia do ostatniego odpowiadający zlecenie.  
  
 *nIDConvert*  
 Identyfikator elementu menu Convert.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli serwer rozpoznaje głównej zlecenie, staje się element menu "zlecenie *typename* obiektu" i `nIDVerbMin` polecenia jest wysyłany, gdy użytkownik wybierze polecenie. Jeśli serwer rozpoznaje kilku poleceń, a następnie staje się element menu " *typename* obiektu" i podmenu wszystkie zlecenia jest wyświetlany, gdy użytkownik wybierze polecenie. Gdy użytkownik wybierze zlecenia z podmenu `nIDVerbMin` są wysyłane, jeśli wybrano opcję pierwsze zlecenie, `nIDVerbMin` + 1 jest wysyłane, jeśli drugi zlecenie jest wybrane i tak dalej. Wartość domyślna `COleDocument` implementacji automatycznie obsługuje tę funkcję.  
  
 Musi mieć następującą instrukcję w skrypcie zasobów aplikacji klienta (. Plik RC):  
  
 **#include \<afxolecl.rc >**  

### <a name="requirements"></a>Wymagania  
 **Nagłówek**: afxole.h 

## <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md)

## <a name="afxoleunlockcontrol"></a>Afxoleunlockcontrol —
Umożliwia odblokowanie fabryki klasy określonego formantu.  
   
### <a name="syntax"></a>Składnia  
  ```
BOOL AFXAPI AfxOleUnlockControl( REFCLSID clsid );  
BOOL AFXAPI AfxOleUnlockControl( LPCTSTR lpszProgID );  
```
### <a name="parameters"></a>Parametry  
 `clsid`  
 Identyfikator unikatowy klasy formantu.  
  
 `lpszProgID`  
 Unikatowy identyfikator formantu.  
   
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli fabryka klas formantu został pomyślnie odblokowane; w przeciwnym razie 0.  
   
### <a name="remarks"></a>Uwagi  
 Formant jest zablokowany z `AfxOleLockControl`, dzięki czemu utworzony dynamicznie dane skojarzone z formantem pozostaje w pamięci. To znacznie przyspieszyć wyświetlanie formantu, ponieważ formant nie muszą utworzona i zniszczona za każdym razem, gdy jest on wyświetlany. Gdy wszystko będzie gotowe do zniszczenia kontrolki wywołania `AfxOleUnlockControl`.  
   
### <a name="example"></a>Przykład  
 ```cpp
// Unlock control's (Microsoft Calendar Control) class factory.

AfxOleUnlockControl(_T("MSCAL.Calendar"));

```
   
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** < afxwin.h >  
   
### <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne](mfc-macros-and-globals.md)  
 [Afxolelockcontrol —](#afxolelockcontrol)

