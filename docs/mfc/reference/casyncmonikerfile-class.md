---
title: Klasa CAsyncMonikerFile | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CAsyncMonikerFile
- AFXOLE/CAsyncMonikerFile
- AFXOLE/CAsyncMonikerFile::CAsyncMonikerFile
- AFXOLE/CAsyncMonikerFile::Close
- AFXOLE/CAsyncMonikerFile::GetBinding
- AFXOLE/CAsyncMonikerFile::GetFormatEtc
- AFXOLE/CAsyncMonikerFile::Open
- AFXOLE/CAsyncMonikerFile::CreateBindStatusCallback
- AFXOLE/CAsyncMonikerFile::GetBindInfo
- AFXOLE/CAsyncMonikerFile::GetPriority
- AFXOLE/CAsyncMonikerFile::OnDataAvailable
- AFXOLE/CAsyncMonikerFile::OnLowResource
- AFXOLE/CAsyncMonikerFile::OnProgress
- AFXOLE/CAsyncMonikerFile::OnStartBinding
- AFXOLE/CAsyncMonikerFile::OnStopBinding
dev_langs:
- C++
helpviewer_keywords:
- CAsyncMonikerFile [MFC], CAsyncMonikerFile
- CAsyncMonikerFile [MFC], Close
- CAsyncMonikerFile [MFC], GetBinding
- CAsyncMonikerFile [MFC], GetFormatEtc
- CAsyncMonikerFile [MFC], Open
- CAsyncMonikerFile [MFC], CreateBindStatusCallback
- CAsyncMonikerFile [MFC], GetBindInfo
- CAsyncMonikerFile [MFC], GetPriority
- CAsyncMonikerFile [MFC], OnDataAvailable
- CAsyncMonikerFile [MFC], OnLowResource
- CAsyncMonikerFile [MFC], OnProgress
- CAsyncMonikerFile [MFC], OnStartBinding
- CAsyncMonikerFile [MFC], OnStopBinding
ms.assetid: 17378b66-a49a-4b67-88e3-7756ad26a2fc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 765f88ef021b333a563fd92f7e9c7806960902e1
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36956986"
---
# <a name="casyncmonikerfile-class"></a>Klasa CAsyncMonikerFile
Zapewnia funkcje do użytku monikery asynchroniczne w formantach ActiveX (dawniej formanty OLE).  
  
## <a name="syntax"></a>Składnia  
  
```  
class CAsyncMonikerFile : public CMonikerFile  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAsyncMonikerFile::CAsyncMonikerFile](#casyncmonikerfile)|Konstruuje `CAsyncMonikerFile` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAsyncMonikerFile::Close](#close)|Zamyka i zwalnia wszystkie zasoby.|  
|[CAsyncMonikerFile::GetBinding](#getbinding)|Pobiera wskaźnik do transferu asynchronicznego powiązania.|  
|[CAsyncMonikerFile::GetFormatEtc](#getformatetc)|Pobiera format danych w strumieniu.|  
|[CAsyncMonikerFile::Open](#open)|Otwiera plik asynchronicznie.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAsyncMonikerFile::CreateBindStatusCallback](#createbindstatuscallback)|Tworzy obiekt COM, który implementuje `IBindStatusCallback`.|  
|[CAsyncMonikerFile::GetBindInfo](#getbindinfo)|Metoda wywoływana przez biblioteki OLE systemu do żądania informacji na temat rodzaju powiązania ma zostać utworzony.|  
|[CAsyncMonikerFile::GetPriority](#getpriority)|Metoda wywoływana przez biblioteki OLE systemu można pobrać priorytet powiązania.|  
|[CAsyncMonikerFile::OnDataAvailable](#ondataavailable)|Wywoływane w celu dostarczania danych po jej udostępnieniu do klienta podczas operacji bind asynchronicznego.|  
|[CAsyncMonikerFile::OnLowResource](#onlowresource)|Wywoływane, gdy zasoby są małe.|  
|[CAsyncMonikerFile::OnProgress](#onprogress)|Wywołuje się, by wskazać proces pobierania danych.|  
|[CAsyncMonikerFile::OnStartBinding](#onstartbinding)|Wywoływane, gdy rozpoczyna się wiązanie.|  
|[CAsyncMonikerFile::OnStopBinding](#onstopbinding)|Wywoływane, gdy zatrzymano transfer asynchronicznego.|  
  
## <a name="remarks"></a>Uwagi  
 Pochodzące z [CMonikerFile](../../mfc/reference/cmonikerfile-class.md), który z kolei jest określana na podstawie [COleStreamFile](../../mfc/reference/colestreamfile-class.md), `CAsyncMonikerFile` używa [imoniker —](http://msdn.microsoft.com/library/windows/desktop/ms679705) interfejsu dostępu dowolny strumień danych do asynchronicznie w tym asynchroniczne ładowanie plików z adresu URL. Pliki mogą być ścieżki danych właściwości formantów ActiveX.  
  
 Monikery asynchroniczne są używane głównie w przypadku aplikacji korzystających z Internetu i formantów ActiveX do zapewnienia reakcji interfejsu użytkownika podczas transferu plików. Podstawowym przykładem jest użycie [CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md) zapewnienie właściwości asynchronicznego dla formantów ActiveX. `CDataPathProperty` Obiektu wielokrotnie otrzyma wskazująca dostępności nowych danych podczas procesu wymiany właściwości długie wywołania zwrotnego.  
  
 Aby uzyskać więcej informacji o sposobie używania monikery asynchroniczne i formantów w aplikacji internetowych zobacz następujące artykuły:  
  
- [Internet pierwszych kroków: Monikery asynchroniczne](../../mfc/asynchronous-monikers-on-the-internet.md)  
  
- [Internet pierwszych kroków: Formanty ActiveX](../../mfc/activex-controls-on-the-internet.md)  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [Cfile —](../../mfc/reference/cfile-class.md)  
  
 [COleStreamFile](../../mfc/reference/colestreamfile-class.md)  
  
 [CMonikerFile](../../mfc/reference/cmonikerfile-class.md)  
  
 `CAsyncMonikerFile`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxole.h  
  
##  <a name="casyncmonikerfile"></a>  CAsyncMonikerFile::CAsyncMonikerFile  
 Konstruuje `CAsyncMonikerFile` obiektu.  
  
```  
CAsyncMonikerFile();
```  
  
### <a name="remarks"></a>Uwagi  
 Nie tworzy `IBindHost` interfejsu. `IBindHost` jest używany tylko wtedy, gdy w podaj `Open` funkcję elementu członkowskiego.  
  
 Opis `IBindHost` interfejsu, zobacz zestaw Windows SDK.  
  
##  <a name="close"></a>  CAsyncMonikerFile::Close  
 Wywołanie tej funkcji, aby zamknąć i zwolnić wszystkie zasoby.  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>Uwagi  
 Można wywołać w plikach nieotwarte lub już zamknięty.  
  
##  <a name="createbindstatuscallback"></a>  CAsyncMonikerFile::CreateBindStatusCallback  
 Tworzy obiekt COM, który implementuje `IBindStatusCallback`.  
  
```  
virtual IUnknown* CreateBindStatusCallback(IUnknown* pUnkControlling);
```  
  
### <a name="parameters"></a>Parametry  
 *pUnkControlling*  
 Wskaźnik do kontrolowania Nieznany (zewnętrznego `IUnknown`) lub **NULL** Jeśli nie jest używana agregacja.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli *pUnkControlling* nie jest **NULL**, funkcja zwraca wskaźnik do wewnętrznej `IUnknown` na nowe obsłudze COM obiektu `IBindStatusCallback`. Jeśli `pUnkControlling` jest **NULL**, funkcja zwraca wskaźnik do `IUnknown` na nowe obsłudze COM obiektu `IBindStatusCallback`.  
  
### <a name="remarks"></a>Uwagi  
 `CAsyncMonikerFile` wymaga obiektu modelu COM, który implementuje `IBindStatusCallback`. MFC implementuje takiego obiektu i będzie się agregowaniu. Można zastąpić `CreateBindStatusCallback` do zwrócenia obiektu COM. Obiekt COM może agregować implementacji MFC, wywołując `CreateBindStatusCallback` z kontrolowanie nieznanego obiektu COM. Obiekty COM implementowane za pomocą `CCmdTarget` obsługi modelu COM można pobrać kontrolowanie nieznany za pomocą `CCmdTarget::GetControllingUnknown`.  
  
 Alternatywnie obiektu modelu COM można delegować do implementacji MFC przez wywołanie metody `CreateBindStatusCallback( NULL )`.  
  
 [CAsyncMonikerFile::Open](#open) wywołania `CreateBindStatusCallback`.  
  
 Aby uzyskać więcej informacji na temat monikery asynchroniczne i wiązania asynchronicznego, zobacz [IBindStatusCallback](http://msdn.microsoft.com/library/ie/ms775060) interfejsu i [sposób wiązania asynchronicznego i Praca magazynu](http://msdn.microsoft.com/library/windows/desktop/aa379152). Aby uzyskać informacje dotyczące agregacji, zobacz [agregacji](http://msdn.microsoft.com/library/windows/desktop/ms686558). Wszystkie trzy tematy znajdują się w zestawie SDK systemu Windows.  
  
##  <a name="getbindinfo"></a>  CAsyncMonikerFile::GetBindInfo  
 Wywoływana z klienta asynchroniczne moniker mówić asynchroniczne krótkiej nazwy, jak chce powiązać.  
  
```  
virtual DWORD GetBindInfo() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Pobiera ustawienia `IBindStatusCallBack`. Opis `IBindStatusCallback` interfejsu, zobacz zestaw Windows SDK.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja ustawia powiązanie asynchroniczne do użycia nośnika magazynowania (strumień) oraz do korzystania z modelu wypychania danych. Należy przesłonić tę funkcję, jeśli chcesz zmienić zachowanie wiązania.  
  
 Jedną z przyczyn w ten sposób będzie można powiązać, przy użyciu model ściągania danych zamiast wypychanie danych modelu. Model ściągania danych klienta dyski Operacja powiązania i krótka nazwa zawiera tylko dane do klienta została przeczytana. W modelu wypychania danych moniker dyski operacja asynchronicznego powiązania i stale powiadamia klient zawsze, gdy nowe dane są dostępne.  
  
##  <a name="getbinding"></a>  CAsyncMonikerFile::GetBinding  
 Wywołanie tej funkcji można pobrać wskaźnik do transferu asynchronicznego powiązania.  
  
```  
IBinding* GetBinding() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do `IBinding` interfejs dostarczony po rozpoczęciu transferu asynchronicznego. Zwraca **NULL** Jeśli jakiegokolwiek powodu przeniesienia nie mogą dopuszczać asynchronicznie.  
  
### <a name="remarks"></a>Uwagi  
 Dzięki temu do transferu danych za pomocą formantu `IBinding` interfejsu, na przykład z `IBinding::Abort`, `IBinding::Pause`, i `IBinding::Resume`.  
  
 Opis `IBinding` interfejsu, zobacz zestaw Windows SDK.  
  
##  <a name="getformatetc"></a>  CAsyncMonikerFile::GetFormatEtc  
 Wywołanie tej funkcji do pobrania formatu danych w strumieniu.  
  
```  
FORMATETC* GetFormatEtc() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do struktury Windows [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) dla aktualnie otwartą strumienia. Zwraca **NULL** czy moniker nie został powiązany, jeśli nie jest asynchroniczny, czy operacja asynchroniczna nie zostało uruchomione.  
  
##  <a name="getpriority"></a>  CAsyncMonikerFile::GetPriority  
 Wywołane z klienta asynchroniczne moniker proces wiązania po uruchomieniu do odbierania pierwszeństwa do wątku dla operacji wiązania.  
  
```  
virtual LONG GetPriority() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Priorytet, w którym odbędzie się transferu asynchronicznego. Jedną z flag priorytet wątku standardowe: **THREAD_PRIORITY_ABOVE_NORMAL**, **THREAD_PRIORITY_BELOW_NORMAL**, **THREAD_PRIORITY_HIGHEST**,  **THREAD_PRIORITY_IDLE**, **THREAD_PRIORITY_LOWEST**, **THREAD_PRIORITY_NORMAL**, i **THREAD_PRIORITY_TIME_CRITICAL**. Zobacz opis funkcji Windows [wykonanie funkcji SetThreadPriority](http://msdn.microsoft.com/library/windows/desktop/ms686277) opis tych wartości.  
  
### <a name="remarks"></a>Uwagi  
 `GetPriority` nie należy wywoływać bezpośrednio. **THREAD_PRIORITY_NORMAL** jest zwracany przez domyślne wdrożenie.  
  
##  <a name="ondataavailable"></a>  CAsyncMonikerFile::OnDataAvailable  
 Wywołuje asynchroniczną moniker `OnDataAvailable` dostarczający dane do klienta po jej udostępnieniu, podczas asynchronicznego powiązanie operacji.  
  
```  
virtual void OnDataAvailable(DWORD dwSize, DWORD bscfFlag);
```  
  
### <a name="parameters"></a>Parametry  
 *dwSize*  
 Zbiorcza ilość (w bajtach) dostępne od początku powiązania danych. Może być równa zero, wskazującą, czy ilość danych nie jest ważna dla operacji lub uzyskiwali nie określonej ilości.  
  
 *bscfFlag*  
 A **BSCF** wartości wyliczenia. Może to być jeden lub więcej z następujących wartości:  
  
- **BSCF_FIRSTDATANOTIFICATION** identyfikuje w pierwszym wywołaniu `OnDataAvailable` wiązania danej operacji.  
  
- **BSCF_INTERMEDIATEDATANOTIFICATION** identyfikuje pośredniczące wywołanie `OnDataAvailable` dla operacji wiązania.  
  
- **BSCF_LASTDATANOTIFICATION** identyfikuje ostatnim wywołaniem `OnDataAvailable` dla operacji wiązania.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja ta funkcja nie działa. Zobacz poniższy przykład dla implementacji próbki.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCWinInet#5](../../mfc/codesnippet/cpp/casyncmonikerfile-class_1.cpp)]  
  
##  <a name="onlowresource"></a>  CAsyncMonikerFile::OnLowResource  
 Metoda wywoływana przez moniker, gdy zasoby są małe.  
  
```  
virtual void OnLowResource();
```  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja wywołuje `GetBinding( )-> Abort( )`.  
  
##  <a name="onprogress"></a>  CAsyncMonikerFile::OnProgress  
 Metoda wywoływana przez moniker wielokrotnie, aby wskazać Bieżący postęp tej operacji bind, zwykle w odpowiednich odstępach czasu w trakcie długotrwałej operacji.  
  
```  
virtual void OnProgress(
    ULONG ulProgress,  
    ULONG ulProgressMax,  
    ULONG ulStatusCode,  
    LPCTSTR szStatusText);
```  
  
### <a name="parameters"></a>Parametry  
 *ulProgress*  
 Wskazuje bieżący postęp operacji bind względem maksymalna oczekiwana wartość podana w *ulProgressMax*.  
  
 *ulProgressMax*  
 Wskazuje oczekiwany maksymalną wartość *ulProgress* na czas trwania wywołań `OnProgress` dla tej operacji.  
  
 *ulStatusCode*  
 Zawiera dodatkowe informacje dotyczące postępu operacji wiązania. Prawidłowe wartości są pobierane z `BINDSTATUS` wyliczenia. Możliwe wartości można znaleźć w temacie uwagi.  
  
 *szStatusText*  
 Informacje o bieżącym postępu, w zależności od wartości *ulStatusCode*. Możliwe wartości można znaleźć w temacie uwagi.  
  
### <a name="remarks"></a>Uwagi  
 Możliwe wartości *ulStatusCode* (i *szStatusText* dla każdej wartości) są:  
  
 **BINDSTATUS_FINDINGRESOURCE**  
 Operacja powiązania jest znajdowania zasobów, która przechowuje obiekt lub magazynu jest powiązana z. *SzStatusText* zawiera nazwę wyświetlaną zasobu przeszukiwany dla (na przykład "www.microsoft.com").  
  
 **BINDSTATUS_CONNECTING**  
 Operacja powiązania nawiązuje połączenie z zasobem, który przechowuje obiekt lub magazynu jest powiązana z. *SzStatusText* zawiera nazwę wyświetlaną zasobu podłączonych do (na przykład adres IP).  
  
 **BINDSTATUS_SENDINGREQUEST**  
 Operacja powiązania żąda obiektu lub magazynu jest powiązana z. *SzStatusText* zawiera nazwę wyświetlaną obiektu (na przykład nazwa pliku).  
  
 **BINDSTATUS_REDIRECTING**  
 Operacja powiązania został przekierowany do lokalizacji innych danych. *SzStatusText* zawiera nazwę wyświetlaną nową lokalizację danych.  
  
 **BINDSTATUS_USINGCACHEDCOPY**  
 Operacja powiązania pobiera żądanego obiektu lub pamięci masowej z kopii w pamięci podręcznej. *SzStatusText* jest **NULL**.  
  
 **BINDSTATUS_BEGINDOWNLOADDATA**  
 Operacja powiązania rozpoczął odbieranie obiektu lub magazynu jest powiązana z. *SzStatusText* zawiera nazwę wyświetlaną lokalizacji danych.  
  
 **BINDSTATUS_DOWNLOADINGDATA**  
 Operacja powiązania w dalszym ciągu otrzymywać obiekt lub magazynu jest powiązana z. *SzStatusText* zawiera nazwę wyświetlaną lokalizacji danych.  
  
 **BINDSTATUS_ENDDOWNLOADDATA**  
 Operacja powiązania zakończył odbieranie obiektu lub magazynu jest powiązana z. *SzStatusText* zawiera nazwę wyświetlaną lokalizacji danych.  
  
 **BINDSTATUS_CLASSIDAVAILABLE**  
 Wystąpienie obiektu związany jest po prostu ma zostać utworzony. *SzStatusText* udostępnia CLSID nowego obiektu w postaci ciągu, co pozwala klientowi możliwość anulowania operacji wiązania w razie potrzeby.  
  
##  <a name="onstartbinding"></a>  CAsyncMonikerFile::OnStartBinding  
 Przesłonić tę funkcję w Twojej klasy pochodne do wykonania akcji, gdy rozpoczyna się wiązanie.  
  
```  
virtual void OnStartBinding();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja jest wywoływana ponownie przy użyciu krótkiej nazwy. Domyślna implementacja nie działa.  
  
##  <a name="onstopbinding"></a>  CAsyncMonikerFile::OnStopBinding  
 Metoda wywoływana przez krótkiej nazwy w końcu Operacja powiązania.  
  
```  
virtual void OnStopBinding(HRESULT hresult, LPCTSTR szError);
```  
  
### <a name="parameters"></a>Parametry  
 *HRESULT*  
 `HRESULT` Oznacza to błąd lub ostrzeżenie wartość.  
  
 *szErrort*  
 Ciąg znaków opisem błędu.  
  
### <a name="remarks"></a>Uwagi  
 Zastąpienie tej funkcji do wykonania akcji, gdy zatrzymano transfer. Domyślnie funkcja zwalnia `IBinding`.  
  
 Opis `IBinding` interfejsu, zobacz zestaw Windows SDK.  
  
##  <a name="open"></a>  CAsyncMonikerFile::Open  
 Wywołanie tej funkcji elementu członkowskiego, aby otworzyć plik asynchronicznie.  
  
```  
virtual BOOL Open(
    LPCTSTR lpszURL,
    CFileException* pError = NULL);
 
virtual BOOL Open(
    IMoniker* pMoniker,
    CFileException* pError = NULL);
 
virtual BOOL Open(
    LPCTSTR lpszURL,
    IBindHost* pBindHost,
    CFileException* pError = NULL);
 
virtual BOOL Open(
    IMoniker* pMoniker,
    IBindHost* pBindHost,
    CFileException* pError = NULL);
 
virtual BOOL Open(
    LPCTSTR lpszURL,
    IServiceProvider* pServiceProvider,
    CFileException* pError = NULL);
 
virtual BOOL Open(
    IMoniker* pMoniker,
    IServiceProvider* pServiceProvider,
    CFileException* pError = NULL);
 
virtual BOOL Open(
    LPCTSTR lpszURL,
    IUnknown* pUnknown,
    CFileException* pError = NULL);
 
virtual BOOL Open(
    IMoniker* pMoniker,
    IUnknown* pUnknown,
    CFileException* pError = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszURL*  
 Wskaźnik do otwarcia asynchronicznie. Plik może być prawidłowym adresem URL lub nazwa pliku.  
  
 *pError*  
 Wskaźnik do wyjątków pliku. W przypadku wystąpienia błędu zostanie ustawiona do przyczyna.  
  
 *pMoniker*  
 Wskaźnik do interfejsu asynchroniczne moniker `IMoniker`, dokładne krótkiej nazwy stanowiący połączenie krótkiej nazwy tego dokumentu, który można pobrać z `IOleClientSite::GetMoniker(OLEWHICHMK_CONTAINER)`i krótka nazwa utworzone na podstawie nazwy ścieżki. Formantu można używać tego krótkiej nazwy do powiązania, ale nie jest to moniker zapisywaniu formantu.  
  
 *pBindHost*  
 Wskaźnik do `IBindHost` interfejs, który będzie używany do tworzenia moniker z potencjalnie względną nazwę ścieżki. Jeśli host powiązania jest nieprawidłowy lub nie ma krótka nazwa, wywołanie domyślnie `Open(lpszFileName,pError)`. Opis `IBindHost` interfejsu, zobacz zestaw Windows SDK.  
  
 *pServiceProvider*  
 Wskaźnik do `IServiceProvider` interfejsu. Jeśli dostawca usług jest nieprawidłowy lub nie powiedzie się w stanie wykonać usługi dla `IBindHost`, domyślnie wywołanie `Open(lpszFileName,pError)`.  
  
 *pUnknown*  
 Wskaźnik do `IUnknown` interfejsu. Jeśli `IServiceProvider` zostanie znaleziony, funkcja zapytań dotyczących `IBindHost`. Jeśli dostawca usług jest nieprawidłowy lub nie powiedzie się w stanie wykonać usługi dla `IBindHost`, domyślnie wywołanie `Open(lpszFileName,pError)`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli plik jest otwarty pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 To wywołanie inicjuje proces wiązania.  
  
 Możesz użyć adresu URL lub nazwę pliku dla *lpszURL* parametru. Na przykład:  
  
 [!code-cpp[NVC_MFCWinInet#6](../../mfc/codesnippet/cpp/casyncmonikerfile-class_2.cpp)]  
  
 - lub -  
  
 [!code-cpp[NVC_MFCWinInet#7](../../mfc/codesnippet/cpp/casyncmonikerfile-class_3.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CMonikerFile](../../mfc/reference/cmonikerfile-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CMonikerFile](../../mfc/reference/cmonikerfile-class.md)   
 [Klasa CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md)
