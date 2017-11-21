---
title: "Usługi modelu obiektów czasu wykonywania | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.mfc.macros
dev_langs: C++
helpviewer_keywords: run-time object model services macros
ms.assetid: 4a3e79df-2ee3-43a4-8193-20298828de85
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ce8ca431a8bdecf2330be67b3ac46ccc394bde91
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="run-time-object-model-services"></a>Usługi modelu obiektów czasu wykonywania
Klasy [CObject](../../mfc/reference/cobject-class.md) i [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) Hermetyzowanie kilka usług obiektu, w tym do uzyskiwania dostępu do informacji o klasie czasu wykonywania serializacji i dynamiczne tworzenie obiektów. Wszystkie klasy wyprowadzone z `CObject` dziedziczy tej funkcji.  
  
 Dostęp do informacji o klasie czasu wykonywania umożliwia określenie informacji na temat klasy obiektów w czasie wykonywania. Możliwość określenia klasy obiektów zawartych w czasie wykonywania jest przydatne, gdy potrzebne są dodatkowe typ kontroli argumentów funkcji i kiedy należy napisać kod specjalnych oparty na klasie obiektu. Informacje o klasie czasu wykonywania nie jest obsługiwana bezpośrednio za pomocą języka C++.  
  
 Serializacja jest proces zapisu lub odczytu zawartości obiektu do lub z pliku. Serializacja służy do przechowywania zawartości obiektu nawet po zamknięciu aplikacji. Obiekt następnie można odczytać z pliku, po ponownym uruchomieniu aplikacji. Takie obiekty danych są określane jako "stałe".  
  
 Dynamiczne tworzenie obiektów można utworzyć obiekt klasy określonej w czasie wykonywania. Na przykład dokument, widoku i ramki obiektów musi obsługiwać dynamicznego tworzenia ponieważ platformę musi utworzyć ich dynamicznie.  
  
 W poniższej tabeli wymieniono makr MFC, które obsługuje informacje o klasie czasu wykonywania serializacji i dynamicznego tworzenia.  
  
 Aby uzyskać więcej informacji o tych obiektów czasu wykonywania usług i serializacji, zobacz artykuł [klasa CObject: uzyskiwanie dostępu do środowiska wykonawczego informacje o klasie](../../mfc/accessing-run-time-class-information.md).  
  
### <a name="run-time-object-model-services-macros"></a>Makra usługi modelu obiektów czasu wykonywania  
  


|||  
|-|-|  
|[DECLARE_DYNAMIC —](#declare_dynamic)|Zapewnia dostęp do informacji o klasie czasu wykonywania (należy użyć w deklaracji klasy).|  
|[DECLARE_DYNCREATE —](#declare_dyncreate)|Umożliwia tworzenie dynamicznych i dostęp do informacji o klasie czasu wykonywania (należy użyć w deklaracji klasy).|  
|[DECLARE_SERIAL —](#declare_serial)|Umożliwia dostęp do informacji o klasie czasu wykonywania (należy użyć w deklaracji klasy) i serializacji.|  
|[IMPLEMENT_DYNAMIC —](#implement_dynamic)|Zapewnia dostęp do informacji o klasie czasu wykonywania (musi być zastosowany w implementacji klasy).|  
|[IMPLEMENT_DYNCREATE —](#implement_dyncreate)|Umożliwia tworzenie dynamicznych i dostęp do informacji dotyczących środowiska wykonawczego (musi być zastosowany w implementacji klasy).|  
|[IMPLEMENT_SERIAL —](#implement_serial)|Zezwala na dostęp do informacji o klasie czasu wykonywania (musi być zastosowany w implementacji klasy) i serializacji.|  
|[RUNTIME_CLASS —](#runtime_class)|Zwraca `CRuntimeClass` struktura umożliwiająca o nazwie klasy.|  


 OLE często wymaga dynamiczne tworzenie obiektów w czasie wykonywania. Na przykład aplikacja serwera OLE musi być można dynamicznie utworzyć elementy OLE w odpowiedzi na żądanie od klienta. Podobnie serwer automatyzacji musi mieć możliwość tworzenia elementów w odpowiedzi na żądania od klientów automatyzacji.  
  
 Microsoft Foundation Class Library zapewnia dwa makra określonych OLE.  
  
### <a name="dynamic-creation-of-ole-objects"></a>Dynamiczne tworzenie obiektów OLE  

 






|||  
|-|-|  
|[AFX_COMCTL32_IF_EXISTS —](#afx_comctl32_if_exists)|Określa, czy biblioteka formantów standardowych implementuje określonego interfejsu API.|
|[AFX_COMCTL32_IF_EXISTS2 —](#afx_comctl32_if_exists2)|Określa, czy biblioteka formantów standardowych implementuje określonego interfejsu API.|
|[DECLARE_OLECREATE —](#declare_olecreate)|Umożliwia obiektów, które ma zostać utworzony za pomocą automatyzacji OLE.|  
|[DECLARE_OLECTLTYPE —](#declare_olectltype)|Deklaruje **getusertypenameid —** i `GetMiscStatus` funkcji elementów członkowskich klasy formantu.|
|[DECLARE_PROPPAGEIDS —](#declare_proppageids)|Deklaruje, że formant OLE zawiera listę właściwości strony, aby wyświetlić jego właściwości.|
|[IMPLEMENT_OLECREATE —](#implement_olecreate)|Umożliwia tworzenie przez OLE system obiektów.|  
|[IMPLEMENT_OLECTLTYPE —](#implement_olectltype)|Implementuje **getusertypenameid —** i `GetMiscStatus` funkcji elementów członkowskich klasy formantu.|  
|[IMPLEMENT_OLECREATE_FLAGS —](#implement_olecreate_flags)|Albo to makro lub [implement_olecreate —](#implement_olecreate) musi występować w pliku implementacji dla każdej klasy, która używa `DECLARE_OLECREATE`. |

## <a name="afx_comctl32_if_exists"></a>AFX_COMCTL32_IF_EXISTS —
Określa, czy biblioteka formantów standardowych implementuje określonego interfejsu API.  
   
### <a name="syntax"></a>Składnia  
  ```  
AFX_COMCTL32_IF_EXISTS(  proc );  
```
### <a name="parameters"></a>Parametry  
 `proc`  
 Wskaźnik do zerem ciąg zawierający nazwę funkcji, lub określa wartość porządkową funkcji. Jeśli ten parametr ma wartość porządkową, musi być w programie word znaczącymi bitami; word znaczących musi mieć wartość zero. Ten parametr musi być w formacie Unicode.  
   
### <a name="remarks"></a>Uwagi  
 Używanie tego makra, aby określić, czy biblioteka formantów standardowych funkcji określonej przez `proc` (zamiast wywoływać metodę [GetProcAddress](http://msdn.microsoft.com/library/windows/desktop/ms683212).  
   
### <a name="requirements"></a>Wymagania  
 afxcomctl32.h, afxcomctl32.inl  
   
### <a name="see-also"></a>Zobacz też  
 [Izolacja wspólnych MFC Określa bibliotekę](../isolation-of-the-mfc-common-controls-library.md) [afx_comctl32_if_exists2 —](#afx_comctl32_if_exists2)
 
## <a name="afx_comctl32_if_exists2"></a>AFX_COMCTL32_IF_EXISTS2 —
Określa, czy biblioteka formantów standardowych implementuje określonego interfejsu API (jest to wersja Unicode [afx_comctl32_if_exists —](#afx_comctl32_if_exists)).  
   
### <a name="syntax"></a>Składnia    
```  
AFX_COMCTL32_IF_EXISTS2( proc );  
```
### <a name="parameters"></a>Parametry  
 `proc`  
 Wskaźnik do zerem ciąg zawierający nazwę funkcji, lub określa wartość porządkową funkcji. Jeśli ten parametr ma wartość porządkową, musi być w programie word znaczącymi bitami; word znaczących musi mieć wartość zero. Ten parametr musi być w formacie Unicode.  
   
### <a name="remarks"></a>Uwagi  
 Używanie tego makra, aby określić, czy biblioteka formantów standardowych funkcji określonej przez `proc` (zamiast wywoływać metodę [GetProcAddress](http://msdn.microsoft.com/library/windows/desktop/ms683212). To makro jest wersja Unicode `AFX_COMCTL32_IF_EXISTS`.  
   
### <a name="requirements"></a>Wymagania  
 afxcomctl32.h, afxcomctl32.inl  
   
### <a name="see-also"></a>Zobacz też  
 [Izolacja wspólnych MFC Określa bibliotekę](../isolation-of-the-mfc-common-controls-library.md) [afx_comctl32_if_exists —](#afx_comctl32_if_exists)



##  <a name="declare_dynamic"></a>DECLARE_DYNAMIC —  
 Dodaje możliwość dostęp do środowiska wykonawczego informacji dotyczących klasę obiektu, gdy wyprowadzanie klasy z `CObject`.  
  
```
DECLARE_DYNAMIC(class_name) 
```  
  
### <a name="parameters"></a>Parametry  
 *class_name*  
 Rzeczywistą nazwą klasy.  
  
### <a name="remarks"></a>Uwagi  
 Dodaj `DECLARE_DYNAMIC` makro modułu nagłówków (.h) dla tej klasy, następnie dołącz ten moduł we wszystkich modułach .cpp wymagających dostępu do obiektów tej klasy.  
  
 Jeśli używasz **DECLARE**_ **dynamiczne** i `IMPLEMENT_DYNAMIC` makra, zgodnie z opisem, można użyć `RUNTIME_CLASS` makro i `CObject::IsKindOf` funkcji, aby określić klasę obiektów wykonywania czas.  
  
 Jeśli `DECLARE_DYNAMIC` znajduje się w deklaracji klasy, następnie `IMPLEMENT_DYNAMIC` muszą być zawarte w implementacji klasy.  
  
 Aby uzyskać więcej informacji na temat `DECLARE_DYNAMIC` makra, zobacz [tematy klasa CObject](../../mfc/using-cobject.md).  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [implement_dynamic —](#implement_dynamic).  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afx.h 

##  <a name="declare_dyncreate"></a>DECLARE_DYNCREATE —  
 Włącza obiektów `CObject`-pochodzi z klasy, które ma zostać utworzony dynamicznie w czasie wykonywania.  
  
```
DECLARE_DYNCREATE(class_name)   
```  
  
### <a name="parameters"></a>Parametry  
 *class_name*  
 Rzeczywistą nazwą klasy.  
  
### <a name="remarks"></a>Uwagi  
 Platformę wykorzystuje tę możliwość do dynamicznego tworzenia nowych obiektów. Na przykład nowy widok utworzony podczas otwierania nowego dokumentu. Klasy ramki dokumentów i widoku powinien obsługiwać dynamicznego tworzenia, ponieważ platformę musi utworzyć je dynamicznie.  
  
 Dodaj `DECLARE_DYNCREATE` makra w module .h dla tej klasy, następnie dołącz ten moduł we wszystkich modułach .cpp wymagających dostępu do obiektów tej klasy.  
  
 Jeśli `DECLARE_DYNCREATE` znajduje się w deklaracji klasy, następnie `IMPLEMENT_DYNCREATE` muszą być zawarte w implementacji klasy.  
  
 Aby uzyskać więcej informacji na temat `DECLARE_DYNCREATE` makra, zobacz [tematy klasa CObject](../../mfc/using-cobject.md).  
  
> [!NOTE]
>  `DECLARE_DYNCREATE` Makro zawiera wszystkie funkcje `DECLARE_DYNAMIC`.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [implement_dyncreate —](#implement_dyncreate).  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afx.h 

 
## <a name="declareolectltype"></a>DECLARE_OLECTLTYPE
Deklaruje **getusertypenameid —** i `GetMiscStatus` funkcji elementów członkowskich klasy formantu.  
   
### <a name="syntax"></a>Składnia    
```
DECLARE_OLECTLTYPE( class_name )  
```
### <a name="parameters"></a>Parametry  
 *class_name*  
 Nazwa klasy formantu.  
   
### <a name="remarks"></a>Uwagi  
 **Getusertypenameid —** i `GetMiscStatus` są czystych funkcji wirtualnych zadeklarowany w `COleControl`. Ponieważ te funkcje są wyłącznie wirtualnych, ich musi zostać zastąpiona w Twojej klasy kontrolki. Oprócz **declare_olectltype —**, należy dodać `IMPLEMENT_OLECTLTYPE` makro użytkownika deklaracja klasy formantu.  
   
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxctl.h  
   
### <a name="see-also"></a>Zobacz też  
 [IMPLEMENT_OLECTLTYPE —](#implement_olectltype)
 

## <a name="declareproppageids"></a>DECLARE_PROPPAGEIDS
Deklaruje, że formant OLE zawiera listę właściwości strony, aby wyświetlić jego właściwości.  
   
### <a name="syntax"></a>Składnia    
```
DECLARE_PROPPAGEIDS( class_name )  
```
### <a name="parameters"></a>Parametry  
 *class_name*  
 Nazwa klasy formantu, który jest właścicielem strony właściwości.  
   
### <a name="remarks"></a>Uwagi  
 Użyj `DECLARE_PROPPAGEIDS` makro końca z deklaracji klasy. Następnie, w pliku .cpp, który definiuje funkcji elementów członkowskich klasy, należy użyć `BEGIN_PROPPAGEIDS` makra, makro wpisy dla każdej strony właściwości formantu i `END_PROPPAGEIDS` makra, aby zadeklarować koniec listy strony właściwości.  
  
 Aby uzyskać więcej informacji na stronach właściwości, zobacz artykuł [formantów ActiveX: strony właściwości](../mfc-activex-controls-property-pages.md).  
   
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxctl.h  
   
### <a name="see-also"></a>Zobacz też   
 [BEGIN_PROPPAGEIDS —](#begin_proppageids)   
 [END_PROPPAGEIDS —](#end_proppageids)

##  <a name="declare_serial"></a>DECLARE_SERIAL —  
 Generuje kod nagłówka C++ niezbędne do `CObject`-klasy, które można serializować.  
  
```
DECLARE_SERIAL(class_name)   
```  
  
### <a name="parameters"></a>Parametry  
 *class_name*  
 Rzeczywistą nazwą klasy.  
  
### <a name="remarks"></a>Uwagi  
 Serializacja jest proces zapisywania lub odczytywania zawartości obiektu do i z pliku.  
  
 Użyj `DECLARE_SERIAL` makra w module .h, a następnie dołącz ten moduł we wszystkich modułach .cpp wymagających dostępu do obiektów tej klasy.  
  
 Jeśli `DECLARE_SERIAL` znajduje się w deklaracji klasy, następnie `IMPLEMENT_SERIAL` muszą być zawarte w implementacji klasy.  
  
 `DECLARE_SERIAL` Makro zawiera wszystkie funkcje `DECLARE_DYNAMIC` i `DECLARE_DYNCREATE`.  
  
 Można użyć **AFX_API** makra, aby automatycznie wyeksportować `CArchive` operator wyodrębniania dla klas używających `DECLARE_SERIAL` i `IMPLEMENT_SERIAL` makra. Nawiasów deklaracje klas (znajdujący się w pliku .h) z następującym kodem:  
  
 [!code-cpp[NVC_MFCCObjectSample#20](../../mfc/codesnippet/cpp/run-time-object-model-services_1.h)]  
  
 Aby uzyskać więcej informacji na temat `DECLARE_SERIAL` makra, zobacz [tematy klasa CObject](../../mfc/using-cobject.md).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCObjectSample#21](../../mfc/codesnippet/cpp/run-time-object-model-services_2.h)]  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afx.h 

##  <a name="implement_dynamic"></a>IMPLEMENT_DYNAMIC —  
 Generuje kod C++ niezbędne do dynamicznym `CObject`-pochodnej klasy środowiska wykonawczego dostęp do nazwy klasy i pozycji w hierarchii.  
  
```
IMPLEMENT_DYNAMIC(class_name, base_class_name)  
```  
  
### <a name="parameters"></a>Parametry  
 *class_name*  
 Rzeczywistą nazwą klasy.  
  
 `base_class_name`  
 Nazwa klasy podstawowej.  
  
### <a name="remarks"></a>Uwagi  
 Użyj `IMPLEMENT_DYNAMIC` makra w .cpp module, a następnie połącz obiekt wynikowy kod tylko raz.  
  
 Aby uzyskać więcej informacji, zobacz [tematy klasa CObject](../../mfc/using-cobject.md).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCObjectSample#2](../../mfc/codesnippet/cpp/run-time-object-model-services_3.h)]  
  
 [!code-cpp[NVC_MFCCObjectSample#3](../../mfc/codesnippet/cpp/run-time-object-model-services_4.cpp)]  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afx.h 

##  <a name="implement_dyncreate"></a>IMPLEMENT_DYNCREATE —  
 Włącza obiektów `CObject`-pochodzi z klasy, które ma zostać utworzony dynamicznie wykonywania czasu, gdy jest używany z `DECLARE_DYNCREATE` makra.  
  
```
IMPLEMENT_DYNCREATE(class_name, base_class_name)   
```  
  
### <a name="parameters"></a>Parametry  
 *class_name*  
 Rzeczywistą nazwą klasy.  
  
 `base_class_name`  
 Rzeczywista nazwa klasy podstawowej.  
  
### <a name="remarks"></a>Uwagi  
 Platforma korzysta z tej możliwości do tworzenia nowych obiektów dynamicznie, na przykład gdy odczytuje obiekt z dysku podczas serializacji. Dodaj `IMPLEMENT_DYNCREATE` makra w pliku implementacji klasy. Aby uzyskać więcej informacji, zobacz [tematy klasa CObject](../../mfc/using-cobject.md).  
  
 Jeśli używasz `DECLARE_DYNCREATE` i `IMPLEMENT_DYNCREATE` makra, można użyć `RUNTIME_CLASS` makro i `CObject::IsKindOf` funkcji członkowskiej, aby określić klasę obiektów w czasie wykonywania.  
  
 Jeśli `DECLARE_DYNCREATE` znajduje się w deklaracji klasy, następnie `IMPLEMENT_DYNCREATE` muszą być zawarte w implementacji klasy.  
  
 Należy pamiętać, że ta definicja makra wywoła domyślnego konstruktora dla klasy. Jeśli nieuproszczony Konstruktor jawnie jest zaimplementowany przez klasę, musi on również jawnie implementować również konstruktora domyślnego. Domyślny konstruktor można dodać do tej klasy **prywatnej** lub **chronione** elementu członkowskiego sekcjach, aby zapobiec wywoływana z poza implementacji klasy.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCObjectSample#22](../../mfc/codesnippet/cpp/run-time-object-model-services_5.h)]  
  
 [!code-cpp[NVC_MFCCObjectSample#23](../../mfc/codesnippet/cpp/run-time-object-model-services_6.cpp)]  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afx.h 

## <a name="implement_olecreate_flags"></a>IMPLEMENT_OLECREATE_FLAGS —
Albo to makro lub [implement_olecreate —](#implement_olecreate) musi występować w pliku implementacji dla każdej klasy, która używa `DECLARE_OLECREATE`.  
   
### <a name="syntax"></a>Składnia    
```
IMPLEMENT_OLECREATE_FLAGS( class_name, external_name, nFlags, 
    l, w1, w2, b1, b2, b3, b4, b5, b6, b7, b8)  
  
```
### <a name="parameters"></a>Parametry  
 *class_name*  
 Rzeczywistą nazwą klasy.  
  
 *external_name*  
 Nazwa obiektu widoczne dla innych aplikacji (ujęta w znaki cudzysłowu).  
  
 `nFlags`  
 Zawiera co najmniej jeden z następujących flag:  
  
-   `afxRegInsertable`Zapewnia kontrolę pojawią się w oknie dialogowym Wstaw obiekt dla obiektów OLE.    
-   `afxRegApartmentThreading`Ustawia model wątkowości w rejestrze ThreadingModel = apartamentu.    
-   **afxregfreethreading —** ustawia model wątkowości w rejestrze ThreadingModel = wolne.  
  
     Możesz połączyć ze sobą dwie flagi `afxRegApartmentThreading` i `afxRegFreeThreading` można ustawić ThreadingModel = jednocześnie. Zobacz [InprocServer32](http://msdn.microsoft.com/library/windows/desktop/ms682390) w zestawie SDK systemu Windows, aby uzyskać więcej informacji o rejestracji modelu wątkowości.    
 *l*, *w1*, *w2*, *b1*, *b2*, *b3*, *b4*, *b5*, *b6*, *b7*, *b8*  
 Składniki klasy **CLSID**.  
   
### <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Jeśli używasz `IMPLEMENT_OLECREATE_FLAGS`, można określić obiektu obsługuje przy użyciu modelu wątkowości `nFlags` parametru. Jeśli chcesz obsługuje tylko treading pojedynczego modelu, użyj `IMPLEMENT_OLECREATE`.  
  
 Zewnętrzna nazwa to identyfikator widoczne dla innych aplikacji. Aplikacje klienckie umożliwia zewnętrzną nazwę żądań z serwera automatyzacji obiektu tej klasy.  
  
 Identyfikator klasy OLE jest unikatowym identyfikatorem 128-bitowego dla obiekt. Składa się z jednego **długi**, dwa **WORD**s i osiem **BAJTÓW**s, reprezentowany przez *l*, *w1*, *w2*, i *b1* za pośrednictwem *b8* w opisie składni. Kreatorzy Kreatora aplikacji i kod tworzy unikatowe identyfikatory klas OLE zgodnie z potrzebami.  
   
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdisp.h  
   
### <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne](mfc-macros-and-globals.md)   
 [DECLARE_OLECREATE —](#declare_olecreate)   
 [Identyfikator CLSID klucza](http://msdn.microsoft.com/library/windows/desktop/ms691424)


## <a name="implement_olecreate"></a>IMPLEMENT_OLECTLTYPE —
Implementuje **getusertypenameid —** i `GetMiscStatus` funkcji elementów członkowskich klasy formantu.  
   
### <a name="syntax"></a>Składnia    
```
DECLARE_OLECTLTYPE( class_name, idsUserTypeName, dwOleMisc )  
```
### <a name="parameters"></a>Parametry  
 *class_name*  
 Nazwa klasy formantu.  
  
 *idsUserTypeName*  
 Identyfikator zasobu ciągu zawierającego nazwę zewnętrznego formantu.  
  
 *dwOleMisc*  
 Wyliczenie zawierający jedną lub więcej flag. Aby uzyskać więcej informacji na ten wyliczenie zobacz [OLEMISC](http://msdn.microsoft.com/library/windows/desktop/ms678497) w zestawie Windows SDK.  
   
### <a name="remarks"></a>Uwagi  
 Oprócz `IMPLEMENT_OLECTLTYPE`, należy dodać **declare_olectltype —** makro użytkownika deklaracja klasy formantu.  
  
 **Getusertypenameid —** funkcji członkowskiej zwraca ciąg zasobu, który identyfikuje Twojej klasy kontrolki. `GetMiscStatus`Zwraca **OLEMISC** usługi bits dla formantu. To wyliczenie Określa kolekcję ustawień opisujące różne właściwości formantu. Aby uzyskać pełny opis **OLEMISC** ustawień, zobacz [OLEMISC](http://msdn.microsoft.com/library/windows/desktop/ms678497) w zestawie Windows SDK.  
  
> [!NOTE]
>  Ustawienia domyślne używane przez ActiveX ControlWizard są: **OLEMISC_ACTIVATEWHENVISIBLE**, **OLEMISC_SETCLIENTSITEFIRST**, **OLEMISC_INSIDEOUT**, **OLEMISC_CANTLINKINSIDE**, i **OLEMISC_RECOMPOSEONRESIZE**.  
   
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxctl.h  
   
### <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne](mfc-macros-and-globals.md)   
 [DECLARE_OLECTLTYPE —](#declare_olectltype)

##  <a name="implement_serial"></a>IMPLEMENT_SERIAL —  
 Generuje kod C++ niezbędne do dynamicznym `CObject`-pochodnej klasy środowiska wykonawczego dostęp do nazwy klasy i pozycji w hierarchii.  
  
```
IMPLEMENT_SERIAL(class_name, base_class_name, wSchema)  
```  
  
### <a name="parameters"></a>Parametry  
 *class_name*  
 Rzeczywistą nazwą klasy.  
  
 `base_class_name`  
 Nazwa klasy podstawowej.  
  
 *wSchema*  
 A **UINT** "numer wersji", który będzie zapisywana w archiwum, aby włączyć program deserializacja do identyfikowania i obsługi danych utworzonych przez program starszych wersji. Liczba schematu klasy nie może być -1.  
  
### <a name="remarks"></a>Uwagi  
 Użyj `IMPLEMENT_SERIAL` makra w .cpp module; następnie połącz wynikowy kod obiektu tylko raz.  
  
 Można użyć **AFX_API** makra, aby automatycznie wyeksportować `CArchive` operator wyodrębniania dla klas używających `DECLARE_SERIAL` i `IMPLEMENT_SERIAL` makra. Nawiasów deklaracje klas (znajdujący się w pliku .h) z następującym kodem:  
  
 [!code-cpp[NVC_MFCCObjectSample#20](../../mfc/codesnippet/cpp/run-time-object-model-services_1.h)]  
  
 Aby uzyskać więcej informacji, zobacz [tematy klasa CObject](../../mfc/using-cobject.md).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCObjectSample#24](../../mfc/codesnippet/cpp/run-time-object-model-services_7.cpp)]  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afx.h 

##  <a name="runtime_class"></a>RUNTIME_CLASS —  
 Pobiera nazwę klasy C++ w strukturze klas środowiska wykonawczego.  
  
```
RUNTIME_CLASS(class_name)  
```  
  
### <a name="parameters"></a>Parametry  
 *class_name*  
 Rzeczywista nazwa klasy (nie ujęta w znaki cudzysłowu).  
  
### <a name="remarks"></a>Uwagi  
 `RUNTIME_CLASS`Zwraca wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) struktury z klasą określoną przez *class_name*. Tylko `CObject`-zadeklarowana z klas pochodnych `DECLARE_DYNAMIC`, `DECLARE_DYNCREATE`, lub `DECLARE_SERIAL` zwróci wskaźniki do `CRuntimeClass` struktury.  
  
 Aby uzyskać więcej informacji, zobacz [tematy klasa CObject](../../mfc/using-cobject.md).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCObjectSample#25](../../mfc/codesnippet/cpp/run-time-object-model-services_8.cpp)]  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afx.h 
   
##  <a name="declare_olecreate"></a>DECLARE_OLECREATE —  
 Włącza obiektów `CCmdTarget`-pochodzi z klasy, które ma zostać utworzony za pomocą automatyzacji OLE.  
  
```
DECLARE_OLECREATE(class_name) 
```  
  
### <a name="parameters"></a>Parametry  
 *class_name*  
 Rzeczywistą nazwą klasy.  
  
### <a name="remarks"></a>Uwagi  
 To makro włącza inne aplikacje korzystające z OLE do tworzenia obiektów tego typu.  
  
 Dodaj `DECLARE_OLECREATE` makra w module .h dla tej klasy, a następnie dołącz ten moduł we wszystkich modułach .cpp wymagających dostępu do obiektów tej klasy.  
  
 Jeśli `DECLARE_OLECREATE` znajduje się w deklaracji klasy, następnie `IMPLEMENT_OLECREATE` muszą być zawarte w implementacji klasy. Deklaracja klasy przy użyciu `DECLARE_OLECREATE` należy również użyć `DECLARE_DYNCREATE` lub `DECLARE_SERIAL`.  

### <a name="requirements"></a>Wymagania  
 **Nagłówek**: afxdisp.h  

##  <a name="implement_olecreate"></a>IMPLEMENT_OLECREATE —  
 Albo to makro lub [implement_olecreate_flags —](#implement_olecreate_flags) musi występować w pliku implementacji dla każdej klasy, która używa `DECLARE_OLECREATE`.  
  
```
IMPLEMENT_OLECREATE(class_name, external_name, l, w1, w2, b1, b2, b3, b4, b5, b6, b7, b8)  
```  
  
### <a name="parameters"></a>Parametry  
 *class_name*  
 Rzeczywistą nazwą klasy.  
  
 *external_name*  
 Nazwa obiektu widoczne dla innych aplikacji (ujęta w znaki cudzysłowu).  
  
 *l*, *w1*, *w2*, *b1*, *b2*, *b3*, *b4*, *b5*, *b6*, *b7*, *b8*  
 Składniki klasy **CLSID**.  
  
### <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Jeśli używasz `IMPLEMENT_OLECREATE`, domyślnie obsługuje tylko jednego modelu wątkowości. Jeśli używasz `IMPLEMENT_OLECREATE_FLAGS`, można określić obiektu obsługuje przy użyciu modelu wątkowości `nFlags` parametru.  
  
 Zewnętrzna nazwa to identyfikator widoczne dla innych aplikacji. Aplikacje klienckie umożliwia zewnętrzną nazwę żądań z serwera automatyzacji obiektu tej klasy.  
  
 Identyfikator klasy OLE jest unikatowym identyfikatorem 128-bitowego dla obiekt. Składa się z jednego **długi**, dwa **WORD**s i osiem **BAJTÓW**s, reprezentowany przez *l*, *w1*, *w2*, i *b1* za pośrednictwem *b8* w opisie składni. Kreatorzy Kreatora aplikacji i kod tworzy unikatowe identyfikatory klas OLE zgodnie z potrzebami.  

### <a name="requirements"></a>Wymagania  
 **Nagłówek**: afxdisp.h 

## <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md)

