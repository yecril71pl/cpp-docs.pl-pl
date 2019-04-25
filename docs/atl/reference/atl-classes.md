---
title: ATL klas i struktur | Dokumentacja firmy Microsoft
ms.date: 05/03/2018
helpviewer_keywords:
- classes [C++], ATL
- ATL, classes
ms.assetid: 7da42e2d-ac84-4506-92bd-502a86d68bdc
ms.openlocfilehash: 561d6cb41ca066f5a2435b4eb1e8710ccaa99ea1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62248943"
---
# <a name="atl-classes-and-structs"></a>Klasy i struktury ATL

Active Template Library (ATL) obejmuje następujące klasy i struktury. Aby znaleźć określonej klasy według kategorii, zobacz [Przegląd klas ATL](../../atl/atl-class-overview.md).

|Klasa / struktura|Opis|Plik nagłówkowy|
|-----------|-----------------|-----------------|
|[ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md)|Zawiera informacje używane do renderowania do różnych celów, takich jak drukarki, metaplik lub kontrolki ActiveX.|atlctl.h|
|[_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md)|Zawiera dane wystąpienia klasy w kodzie obsługi okien w ATL.|atlbase.h|
|[_ATL_BASE_MODULE70](../../atl/reference/atl-base-module70-structure.md)|Używane przez dowolny projekt, który używa ATL.|atlbase.h|
|[_ATL_COM_MODULE70](../../atl/reference/atl-com-module70-structure.md)|Używane przez kod związane z modelu COM w ATL.| atlbase.h|
|[_ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md)|Zawiera informacje o typie opisuje metody lub właściwości na dispinterface.|atlcom.h|
|[_ATL_MODULE70](../../atl/reference/atl-module70-structure.md)|Zawiera dane używane przez każdy moduł ATL.|atlbase.h|
|[_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md)|Używane przez kod obsługi okien w ATL.|atlbase.h|
|[CA2AEX](../../atl/reference/ca2aex-class.md)|Ta klasa jest używana przez makra konwersji ciągów CA2TEX i CT2AEX i typedef CA2A.|atlconv.h|
|[CA2CAEX](../../atl/reference/ca2caex-class.md)|Ta klasa jest używana przez makra konwersji ciągów CA2CTEX i CT2CAEX i typedef CA2CA.|atlconv.h|
|[CA2WEX](../../atl/reference/ca2wex-class.md)|Ta klasa jest używana przez makra konwersji ciągów CA2TEX, CA2CTEX, CT2WEX i CT2CWEX i typedef CA2W.|atlconv.h|
|[CAccessToken](../../atl/reference/caccesstoken-class.md)|Ta klasa jest otoką dla tokenu dostępu.|atlsecurity.h|
|[CAcl](../../atl/reference/cacl-class.md)|Ta klasa jest otoką dla struktury listy kontroli dostępu (listy kontroli dostępu).|atlsecurity.h|
|[CAdapt](../../atl/reference/cadapt-class.md)|Ten szablon jest używany do opakowywania klas, które ponownie definiują operator address-of, aby zwrócić coś innego niż adres obiektu.|atlcomcli.h|
|[CAtlArray](../../atl/reference/catlarray-class.md)|Ta klasa implementuje obiektu array.|atlcoll.h|
|[CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md)|Ta klasa implementuje serwer COM wątków w puli, model przedziału.|atlbase.h|
|[CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md)|Ta klasa dostarcza metody do implementowania serwera wątków w puli, model przedziału COM.|atlbase.h|
|[CAtlBaseModule](../../atl/reference/catlbasemodule-class.md)|Ta klasa jest tworzone w każdym projekcie ATL.|atlcore.h|
|[CAtlComModule](../../atl/reference/catlcommodule-class.md)|Ta klasa implementuje modułu serwera COM.|atlbase.h|
|[CAtlDebugInterfacesModule](../../atl/reference/catldebuginterfacesmodule-class.md)|Ta klasa obsługuje debugowanie interfejsów.|atlbase.h|
|[CAtlDllModuleT](../../atl/reference/catldllmodulet-class.md)|Ta klasa reprezentuje modułu dla biblioteki DLL.|atlbase.h|
|[CAtlException](../../atl/reference/catlexception-class.md)|Ta klasa definiuje wyjątek ATL.|atlexcept.h|
|[CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)|Ta klasa reprezentuje modułu dla aplikacji.|atlbase.h|
|[CAtlFile](../../atl/reference/catlfile-class.md)|Ta klasa dostarcza alokowania elastycznego otokę Windows plików obsługi interfejsu API.|atlfile.h|
|[CAtlFileMapping](../../atl/reference/catlfilemapping-class.md)|Ta klasa reprezentuje plik mapowany w pamięci, dodanie operatora rzutowania do metod [CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md).|atlfile.h|
|[CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)|Ta klasa reprezentuje plik mapowanych na pamięć.|atlfile.h|
|[CAtlList](../../atl/reference/catllist-class.md)|Ta klasa dostarcza metody do tworzenia i zarządzania obiekt listy.|atlcoll.h|
|[CAtlMap](../../atl/reference/catlmap-class.md)|Ta klasa dostarcza metody do tworzenia i zarządzania obiektu mapy.|atlcoll.h|
|[CAtlModule](../../atl/reference/catlmodule-class.md)|Ta klasa udostępnia metody używane przez kilka klasy modułów ALT.|atlbase.h|
|[CAtlModuleT](../../atl/reference/catlmodulet-class.md)|Ta klasa implementuje modułu ATL.|atlbase.h|
|[CAtlPreviewCtrlImpl](../../atl/reference/catlpreviewctrlimpl-class.md)|Ta klasa jest implementacją ATL okna, które jest umieszczone na oknie hosta zapewnionym przez powłokę podglądu sformatowanego.|atlpreviewctrlimpl.h|
|[CAtlServiceModuleT](../../atl/reference/catlservicemodulet-class.md)|Ta klasa implementuje usługi.|atlbase.h|
|[CAtlTemporaryFile](../../atl/reference/catltemporaryfile-class.md)|Ta klasa zawiera metody służące do tworzenia i używania pliku tymczasowego.|atlfile.h|
|[CAtlTransactionManager](../../atl/reference/catltransactionmanager-class.md)|Ta klasa udostępnia otokę dla funkcji Menedżera transakcji jądra (KTM).|atltransactionmanager.h|
|[CAtlWinModule](../../atl/reference/catlwinmodule-class.md)|Ta klasa zapewnia obsługę składników obsługi okien ATL.|atlbase.h|
|[CAutoPtr](../../atl/reference/cautoptr-class.md)|Ta klasa reprezentuje obiekt inteligentnego wskaźnika.|atlbase.h|
|[CAutoPtrArray](../../atl/reference/cautoptrarray-class.md)|Ta klasa dostarcza metody przydatne przy konstruowaniu tablicy inteligentnych wskaźników.|atlbase.h|
|[CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md)|Ta klasa dostarcza metody, funkcje statyczne i definicje typów przydatne podczas tworzenia kolekcji inteligentnych wskaźników.|atlcoll.h|
|[CAutoPtrList](../../atl/reference/cautoptrlist-class.md)|Ta klasa dostarcza metody przydatne podczas tworzenia listy inteligentne wskaźniki.|atlcoll.h|
|[CAutoVectorPtr](../../atl/reference/cautovectorptr-class.md)|Ta klasa reprezentuje obiekt inteligentny wskaźnik przy użyciu nowych wektorów i delete — operatory.|atlbase.h|
|[CAutoVectorPtrElementTraits](../../atl/reference/cautovectorptrelementtraits-class.md)|Ta klasa dostarcza metody, funkcje statyczne i przydatne podczas tworzenia kolekcji inteligentnych wskaźników przy użyciu nowych wektorów i delete — operatory definicje typów.|atlcoll.h|
|[CAxDialogImpl](../../atl/reference/caxdialogimpl-class.md)|Ta klasa implementuje okno dialogowe (modalnym lub niemodalnym), który obsługuje formanty ActiveX.|atlwin.h|
|[CAxWindow](../../atl/reference/caxwindow-class.md)|Ta klasa dostarcza metody do manipulowania okna hostowania kontrolki ActiveX.|atlwin.h|
|[CAxWindow2T](../../atl/reference/caxwindow2t-class.md)|Ta klasa dostarcza metody do manipulowania okno które obsługuje formant ActiveX i ma również obsługę hostowania licencjonowane formanty ActiveX.|atlwin.h|
|[CBindStatusCallback](../../atl/reference/cbindstatuscallback-class.md)|Ta klasa implementuje `IBindStatusCallback` interfejsu.|atlctl.h|
|[CComAggObject](../../atl/reference/ccomaggobject-class.md)|Ta klasa implementuje [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) dla obiektu zagregowanego.|atlcom.h|
|[CComAllocator](../../atl/reference/ccomallocator-class.md)|Ta klasa dostarcza metody do zarządzania ilości pamięci za pomocą procedury pamięci COM.|atlbase.h|
|[CComApartment](../../atl/reference/ccomapartment-class.md)|Ta klasa obsługuje zarządzanie typu apartment w module EXE wątków w puli.|atlbase.h|
|[CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md)|Ta klasa dostarcza metody do uzyskania i zwalniania własności obiektu sekcję krytyczną.|atlcore.h|
|[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)|Począwszy od ATL 7.0 `CComAutoThreadModule` jest przestarzała: zobacz [modułów ATL](../../atl/atl-module-classes.md) Aby uzyskać więcej informacji.|atlbase.h|
|[CComBSTR](../../atl/reference/ccombstr-class.md)|Ta klasa jest otoką BSTR.|atlbase.h|
|[CComCachedTearOffObject](../../atl/reference/ccomcachedtearoffobject-class.md)|Ta klasa implementuje [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) odrywania interfejsu.|atlcom.h|
|[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)|Ta klasa implementuje [IClassFactory](/windows/desktop/api/unknwnbase/nn-unknwnbase-iclassfactory) interfejsu.|atlcom.h|
|[CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)|Ta klasa implementuje [IClassFactory2](/windows/desktop/api/ocidl/nn-ocidl-iclassfactory2) interfejsu.|atlcom.h|
|[CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)|Ta klasa implementuje [IClassFactory](/windows/desktop/api/unknwnbase/nn-unknwnbase-iclassfactory) interfejs i umożliwia tworzenie w apartamentach wielu obiektów.|atlcom.h|
|[CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md)|Ta klasa jest pochodną [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) i używa [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) skonstruowanie pojedynczego obiektu.|atlcom.h|
|[CComCoClass](../../atl/reference/ccomcoclass-class.md)|Ta klasa dostarcza metody do tworzenia wystąpienia klasy i uzyskania jej właściwości.|atlcom.h|
|[CComCompositeControl](../../atl/reference/ccomcompositecontrol-class.md)|Ta klasa dostarcza metody, o których trzeba do zaimplementowania kontrolek złożonych.|atlctl.h|
|[CComContainedObject](../../atl/reference/ccomcontainedobject-class.md)|Ta klasa implementuje [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) przez delegowanie do obiektu właściciela `IUnknown`.|atlcom.h|
|[CComControl](../../atl/reference/ccomcontrol-class.md)|Ta klasa dostarcza metody do tworzenia i zarządzania formantami ATL.|atlctl.h|
|[CComControlBase](../../atl/reference/ccomcontrolbase-class.md)|Ta klasa dostarcza metody do tworzenia i zarządzania formantami ATL.|atlctl.h|
|[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)|Ta klasa dostarcza metody do uzyskania i zwalniania własności obiektu sekcję krytyczną.|atlcore.h|
|[CComCritSecLock](../../atl/reference/ccomcritseclock-class.md)|Ta klasa dostarcza metody do blokowanie i odblokowywanie obiektu sekcję krytyczną.|atlbase.h|
|[CComCurrency](../../atl/reference/ccomcurrency-class.md)|Ta klasa posiada metody i operatorów do tworzenia i zarządzania obiektem waluty.|atlcur.h|
|[CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md)|Ta klasa przechowuje tablicę `IUnknown` wskaźników.|atlcom.h|
|[CComEnum](../../atl/reference/ccomenum-class.md)|Ta klasa definiuje obiekt modułu wyliczającego COM, na podstawie tablicy.|atlcom.h|
|[CComEnumImpl](../../atl/reference/ccomenumimpl-class.md)|Ta klasa zawiera implementację interfejsu modułu wyliczającego COM, gdzie elementy wyliczany są przechowywane w tablicy.|atlcom.h|
|[CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md)|Ta klasa definiuje obiekt modułu wyliczającego COM, na podstawie kolekcji standardowej biblioteki języka C++.|atlcom.h|
|[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)|Ta klasa udostępnia te same metody jako [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) , ale nie zapewnia sekcję krytyczną.|atlcore.h|
|[CComGITPtr](../../atl/reference/ccomgitptr-class.md)|Ta klasa dostarcza metody radzenia sobie z wskaźniki interfejsu i tabeli interfejsu globalnego (GIT).|atlbase.h|
|[CComHeap](../../atl/reference/ccomheap-class.md)|Ta klasa implementuje [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) przy użyciu funkcji alokacji pamięci COM.|ATLComMem.h|
|[CComHeapPtr](../../atl/reference/ccomheapptr-class.md)|Klasa inteligentnego wskaźnika do zarządzania wskaźniki stosu.|atlbase.h|
|[CComModule](../../atl/reference/ccommodule-class.md)|Począwszy od ATL 7.0 `CComModule` jest przestarzała: zobacz [modułów ATL](../../atl/atl-module-classes.md) Aby uzyskać więcej informacji.|atlbase.h|
|[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)|Ta klasa dostarcza metody metodą o bezpiecznych wątkach, zwiększanie i zmniejszanie wartości zmiennej.|atlbase.h|
|[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)|Ta klasa dostarcza metody wątkowo zwiększanie i zmniejszanie wartości zmiennej, bez sekcję krytyczną blokowanie lub odblokowywanie funkcji.|atlbase.h|
|[CComObject](../../atl/reference/ccomobject-class.md)|Ta klasa implementuje `IUnknown` nieagregowane obiektu.|atlcom.h|
|[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)|Ta klasa zarządza moduł zawierający licznik odwołań do Twojej `Base` obiektu.|atlcom.h|
|[CComObjectNoLock](../../atl/reference/ccomobjectnolock-class.md)|Ta klasa implementuje `IUnknown` nieagregowane obiektu, ale ma nie przyrostu liczbę blokad modułu w konstruktorze.|atlcom.h|
|[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)|Ten element typedef dla [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md) jest szablonowana na domyślny model serwera wątków.|atlcom.h|
|[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)|Ta klasa dostarcza metody do obsługi zarządzania liczba odwołanie do obiektu nieagregowane i zagregowane obiekty.|atlcom.h|
|[CComObjectStack](../../atl/reference/ccomobjectstack-class.md)|Ta klasa tworzy tymczasowy obiekt COM i dostarcza mu szkieletowych implementacji `IUnknown`.|atlcom.h|
|[CComPolyObject](../../atl/reference/ccompolyobject-class.md)|Ta klasa implementuje `IUnknown` zagregowane lub nieagregowane w obiekcie.|atlcom.h|
|[CComPtr](../../atl/reference/ccomptr-class.md)|Klasa inteligentnego wskaźnika do zarządzania wskaźniki interfejsu COM.|atlcomcli.h|
|[CComPtrBase](../../atl/reference/ccomptrbase-class.md)|Ta klasa stanowi podstawę dla klas inteligentnego wskaźnika za pomocą procedury opartym na modelu COM pamięci.|atlcomcli.h|
|[CComQIPtr](../../atl/reference/ccomqiptr-class.md)|Klasa inteligentnego wskaźnika do zarządzania wskaźniki interfejsu COM.|atlcomcli.h|
|[CComQIPtrElementTraits](../../atl/reference/ccomqiptrelementtraits-class.md)|Ta klasa dostarcza metody, funkcje statyczne i definicje typów przydatne podczas tworzenia kolekcji wskaźniki interfejsu COM.|atlcoll.h|
|[CComSafeArray](../../atl/reference/ccomsafearray-class.md)|Ta klasa jest otoką `SAFEARRAY Data Type` struktury.|atlsafe.h|
|[CComSafeArrayBound](../../atl/reference/ccomsafearraybound-class.md)|Ta klasa jest otoką `SAFEARRAYBOUND` struktury.|atlsafe.h|
|[CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md)|Ta klasa zarządza wybór wątku dla klasy [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).|atlbase.h|
|[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)|Ta klasa zawiera metody służące do zwiększanie i zmniejszanie, wartość zmiennej.|atlbase.h|
|[CComTearOffObject](../../atl/reference/ccomtearoffobject-class.md)|Ta klasa implementuje interfejs odrywania.|atlcom.h|
|[CComUnkArray](../../atl/reference/ccomunkarray-class.md)|Ta klasa przechowuje `IUnknown` wskaźników i jest przeznaczony do użycia jako parametr do [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) klasy szablonu.|atlcom.h|
|[CComVariant](../../atl/reference/ccomvariant-class.md)|Ta klasa opakowuje Typ VARIANT, zapewniając członka, wskazujący typ danych przechowywanych.|atlcomcli.h|
|[CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md)|Ta klasa implementuje okno znajdujących się w innym obiekcie.|atlwin.h|
|[CCRTAllocator](../../atl/reference/ccrtallocator-class.md)|Ta klasa dostarcza metody do zarządzania ilości pamięci za pomocą procedury pamięci CRT.|atlcore.h|
|[CCRTHeap](../../atl/reference/ccrtheap-class.md)|Ta klasa implementuje [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) przy użyciu stosu CRT.|atlmem.h|
|[CDacl](../../atl/reference/cdacl-class.md)|Ta klasa jest otoką dla struktury DACL (list arbitralnej kontroli dostępu).|atlsecurity.h|
|[Klasa CDebugReportHook](../../atl/reference/cdebugreporthook-class.md)|Klasa jest używana do wysyłania raportów debugowania z nazwanym potokiem.|atlutil.h|
|[CDefaultCharTraits](../../atl/reference/cdefaultchartraits-class.md)|Ta klasa udostępnia dwie funkcje statyczne konwersję znaków między wielkimi i małymi.|atlcoll.h|
|[CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)|Ta klasa udostępnia domyślny element porównanie funkcji.|atlcoll.h|
|[CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)|Ta klasa dostarcza domyślne metody i funkcje dla klas kolekcji.|atlcoll.h|
|[CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)|Ta klasa udostępnia funkcję statyczną do obliczania wartości skrótu.|atlcoll.h|
|[CDialogImpl](../../atl/reference/cdialogimpl-class.md)|Ta klasa dostarcza metody do tworzenia modalne lub niemodalne okno dialogowe.|atlwin.h|
|[CDynamicChain](../../atl/reference/cdynamicchain-class.md)|Ta klasa dostarcza metody obsługi dynamicznego łańcucha mapy komunikatów.|atlwin.h|
|[CElementTraits](../../atl/reference/celementtraits-class.md)|Ta klasa jest używana przez klasy kolekcji do zapewnienia metod i funkcji przenoszenie, kopiowanie, porównanie i operacje wyznaczania wartości skrótu.|atlcoll.h|
|[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)|Ta klasa zawiera kopię domyślnego i przenoszenie metody do klasy kolekcji.|atlcoll.h|
|[CFirePropNotifyEvent](../../atl/reference/cfirepropnotifyevent-class.md)|Ta klasa dostarcza metody do powiadamiania ujścia kontenera odnośnie do zmian właściwości formantu.|atlctl.h|
|[CGlobalHeap](../../atl/reference/cglobalheap-class.md)|Ta klasa implementuje [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) przy użyciu funkcji sterty globalnej Win32.|atlmem.h|
|[CHandle](../../atl/reference/chandle-class.md)|Ta klasa dostarcza metody do tworzenia i używania obiektu uchwyt.|atlbase.h|
|[CHeapPtr](../../atl/reference/cheapptr-class.md)|Klasa inteligentnego wskaźnika do zarządzania wskaźniki stosu.|atlcore.h|
|[CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)|Ta klasa stanowi podstawę kilka klas wskaźnika inteligentnego sterty.|atlcore.h|
|[Klasa CHeapPtrElementTraits](../../atl/reference/cheapptrelementtraits-class.md)|Ta klasa dostarcza metody, funkcje statyczne i definicje typów przydatne podczas tworzenia kolekcji wskaźniki stosu.|atlcoll.h|
|[CHeapPtrList](../../atl/reference/cheapptrlist-class.md)|Ta klasa dostarcza metody przydatne podczas tworzenia listy wskaźników sterty.|atlcoll.h|
|[CImage](../../atl-mfc-shared/reference/cimage-class.md)|Zapewnia obsługę rozszerzonych mapy bitowej, łącznie z możliwością ładowania i zapisać obrazy w formacie JPEG, GIF, BMP i przenośnych Network Graphics (PNG).|atlimage.h|
|[CInterfaceArray](../../atl/reference/cinterfacearray-class.md)|Ta klasa dostarcza metody przydatne przy konstruowaniu tablicy wskaźników interfejsu COM.|atlcoll.h|
|[CInterfaceList](../../atl/reference/cinterfacelist-class.md)|Ta klasa dostarcza metody przydatne podczas tworzenia listy wskaźniki interfejsu COM.|atlcoll.h|
|[CLocalHeap](../../atl/reference/clocalheap-class.md)|Ta klasa implementuje [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) przy użyciu funkcji lokalnej sterty systemu Win32.|atlmem.h|
|[CMessageMap](../../atl/reference/cmessagemap-class.md)|Ta klasa umożliwia mapy wiadomości obiekt dostępu do innego obiektu.|atlwin.h|
|[Klasa CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md)|Odbiera żądania z puli wątków i przekazuje je do obiektu procesu roboczego, który jest tworzona i niszczona przy każdym żądaniu.|atlutil.h|
|[Klasa CNoWorkerThread](../../atl/reference/cnoworkerthread-class.md)|Klasa jest używana jako argument dla `MonitorClass` pamięci podręcznej szablonów parametru klasy, jeśli chcesz wyłączyć obsługi dynamicznej pamięci podręcznej.|atlutil.h|
|[Klasa CPathT](../../atl/reference/cpatht-class.md)|Ta klasa reprezentuje ścieżkę.|atlpath.h|
|[CPrimitiveElementTraits](../../atl/reference/cprimitiveelementtraits-class.md)|Ta klasa dostarcza metody domyślne i funkcji dla klasy kolekcji składa się z pierwotnych typów danych.|atlcoll.h|
|[CPrivateObjectSecurityDesc](../../atl/reference/cprivateobjectsecuritydesc-class.md)|Ta klasa reprezentuje obiekt deskryptora zabezpieczeń obiektu prywatnego.|atlsecurity.h|
|[CRBMap](../../atl/reference/crbmap-class.md)|Ta klasa reprezentuje strukturę mapowania przy użyciu drzewa binarnego Red czarny.|atlcoll.h|
|[CRBMultiMap](../../atl/reference/crbmultimap-class.md)|Ta klasa reprezentuje strukturę mapowania, która umożliwia każdy klucz ma zostać skojarzony z więcej niż jedną wartość, przy użyciu drzewa binarnego Red czarny.|atlcoll.h|
|[CRBTree](../../atl/reference/crbtree-class.md)|Ta klasa dostarcza metody do tworzenia i przy użyciu drzewa Red czarny.|atlcoll.h|
|[CRegKey](../../atl/reference/cregkey-class.md)|Ta klasa dostarcza metody do manipulowania wpisy w rejestrze systemowym.|atlbase.h|
|[CRTThreadTraits](../../atl/reference/crtthreadtraits-class.md)|Ta klasa udostępnia funkcję tworzenia wątku CRT. Jeśli wątek będzie używać funkcji CRT, należy użyć tej klasy.|atlbase.h|
|[CSacl](../../atl/reference/csacl-class.md)|Ta klasa jest otoką dla struktury SACL (systemowa lista kontroli dostępu).|atlsecurity.h|
|[CSecurityAttributes](../../atl/reference/csecurityattributes-class.md)|Ta klasa jest otoką alokowania elastycznego `SECURITY_ATTRIBUTES` struktury.|atlsecurity.h|
|[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)|Ta klasa jest otoką `SECURITY_DESCRIPTOR` struktury.|atlsecurity.h|
|[CSid](../../atl/reference/csid-class.md)|Ta klasa jest otoką `SID` struktury (identyfikator zabezpieczeń).|atlsecurity.h|
|[CSimpleArray](../../atl/reference/csimplearray-class.md)|Ta klasa dostarcza metody do zarządzania macierzą proste.|atlsimpcoll.h|
|[CSimpleArrayEqualHelper](../../atl/reference/csimplearrayequalhelper-class.md)|Ta klasa jest pomocnika dla [CSimpleArray](../../atl/reference/csimplearray-class.md) klasy.|atlsimpcoll.h|
|[CSimpleArrayEqualHelperFalse](../../atl/reference/csimplearrayequalhelperfalse-class.md)|Ta klasa jest pomocnika dla [CSimpleArray](../../atl/reference/csimplearray-class.md) klasy.|atlsimpcoll.h|
|[CSimpleDialog](../../atl/reference/csimpledialog-class.md)|Ta klasa implementuje podstawowe modalne okno dialogowe.|atlwin.h|
|[CSimpleMap](../../atl/reference/csimplemap-class.md)|Ta klasa udostępnia obsługę tablicy mapowania proste.|atlsimpcoll.h|
|[CSimpleMapEqualHelper](../../atl/reference/csimplemapequalhelper-class.md)|Ta klasa jest pomocnika dla [CSimpleMap](../../atl/reference/csimplemap-class.md) klasy.|atlsimpcoll.h|
|[CSimpleMapEqualHelperFalse](../../atl/reference/csimplemapequalhelperfalse-class.md)|Ta klasa jest pomocnika dla [CSimpleMap](../../atl/reference/csimplemap-class.md) klasy.|atlsimpcoll.h|
|[CSnapInItemImpl](../../atl/reference/csnapinitemimpl-class.md)|Ta klasa dostarcza metody implementacji obiektu przystawki węzła.|atlsnap.h|
|[CSnapInPropertyPageImpl](../../atl/reference/csnapinpropertypageimpl-class.md)|Ta klasa dostarcza metody wykonywania obiekt strony właściwości przystawki.|atlsnap.h|
|[CStockPropImpl](../../atl/reference/cstockpropimpl-class.md)|Ta klasa dostarcza metody do obsługi wartości właściwości podstawowych.|atlctl.h|
|[CStringElementTraits](../../atl/reference/cstringelementtraits-class.md)|Ta klasa udostępnia statyczne funkcje używane przez klasy kolekcji przechowywania `CString` obiektów.|cstringt.h|
|[CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md)|Ta klasa dostarcza statyczne funkcje związane z przechowywanych w obiektach klasy kolekcji ciągów. Jest on podobny do [CStringElementTraits](../../atl/reference/cstringelementtraits-class.md), ale wykonuje porównania bez uwzględniania wielkości liter.|atlcoll.h|
|[CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md)|Ta klasa dostarcza statyczne funkcje związane z przechowywanych w obiektach klasy kolekcji ciągów. Obiektów w postaci ciągów są traktowane jako odwołania.|atlcoll.h|
|[Klasa CThreadPool](../../atl/reference/cthreadpool-class.md)|Ta klasa dostarcza puli wątków roboczych, które przetwarzają kolejki elementów roboczych.|atlutil.h|
|[CTokenGroups](../../atl/reference/ctokengroups-class.md)|Ta klasa jest otoką `TOKEN_GROUPS` struktury.|atlsecurity.h|
|[CTokenPrivileges](../../atl/reference/ctokenprivileges-class.md)|Ta klasa jest otoką `TOKEN_PRIVILEGES` struktury.|atlsecurity.h|
|[Klasa CUrl](../../atl/reference/curl-class.md)|Ta klasa reprezentuje adres URL. Umożliwia on manipulowanie każdy element adresu URL, niezależnie od innych, czy analiza kodu istniejącego adresu URL ciąg lub tworzenia ciągu od podstaw.|atlutil.h|
|[CW2AEX](../../atl/reference/cw2aex-class.md)|Ta klasa jest używana przez makra konwersji ciągów CT2AEX, CW2TEX, CW2CTEX i CT2CAEX i typedef CW2A.|atlconv.h|
|[CW2CWEX](../../atl/reference/cw2cwex-class.md)|Ta klasa jest używana przez makra konwersji ciągów CW2CTEX i CT2CWEX i typedef CW2CW.|atlconv.h|
|[CW2WEX](../../atl/reference/cw2wex-class.md)|Ta klasa jest używana przez makra konwersji ciągów CW2TEX i CT2WEX i typedef CW2W.|atlconv.h|
|[CWin32Heap](../../atl/reference/cwin32heap-class.md)|Ta klasa implementuje [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) przy użyciu funkcji alokacji sterty Win32.|atlmem.h|
|[CWindow](../../atl/reference/cwindow-class.md)|Ta klasa dostarcza metody do manipulowania okna.|atlwin.h|
|[CWindowImpl](../../atl/reference/cwindowimpl-class.md)|Ta klasa dostarcza metody do tworzenia lub Tworzenie podklasy okna.|atlwin.h|
|[CWinTraits](../../atl/reference/cwintraits-class.md)|Ta klasa dostarcza metody do standaryzacji stylów używanych podczas tworzenia obiektu okna.|atlwin.h|
|[CWinTraitsOR](../../atl/reference/cwintraitsor-class.md)|Ta klasa dostarcza metody do standaryzacji stylów używanych podczas tworzenia obiektu okna.|atlwin.h|
|[CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)|Ta klasa dostarcza metody do rejestrowania informacji dla klasy okna.|atlwin.h|
|[Klasa CWorkerThread](../../atl/reference/cworkerthread-class.md)|Ta klasa tworzy wątek roboczy lub korzysta z istniejącą grupę, czeka na co najmniej jeden uchwytów obiektu jądra i wykonuje funkcję określonego klienta, gdy jeden z uchwytów, jest sygnalizowane.|atlutil.h|
|[IAtlAutoThreadModule](../../atl/reference/iatlautothreadmodule-class.md)|Ta klasa reprezentuje interfejs dla `CreateInstance` metody.|atlbase.h|
|[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)|Ta klasa reprezentuje interfejs do Menedżera pamięci.|atlmem.h|
|[IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md)|Ten interfejs zapewnia metody do określania właściwości kontrolki hostowanej lub kontenera.|atlbase.h, ATLIFace.h|
|[IAxWinAmbientDispatchEx](../../atl/reference/iaxwinambientdispatchex-interface.md)|Ten interfejs implementuje dodatkowe właściwości otoczenia hostowanej kontrolki.|atlbase.h, ATLIFace.h|
|[IAxWinHostWindow](../../atl/reference/iaxwinhostwindow-interface.md)|Ten interfejs zapewnia metody do manipulowania formantu i jego obiekt hosta.|atlbase.h, ATLIFace.h|
|[IAxWinHostWindowLic](../../atl/reference/iaxwinhostwindowlic-interface.md)|Ten interfejs zapewnia metody do manipulowania licencjonowany formant i jego obiekt hosta.|atlbase.h, ATLIFace.h|
|[ICollectionOnSTLImpl](../../atl/reference/icollectiononstlimpl-class.md)|Ta klasa udostępnia metody używane przez klasę kolekcji.|atlcom.h|
|[IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md)|Ta klasa implementuje kontener punktu połączenia, aby zarządzać kolekcją [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) obiektów.|atlcom.h|
|[IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)|Ta klasa implementuje punkt połączenia.|atlcom.h|
|[IDataObjectImpl](../../atl/reference/idataobjectimpl-class.md)|Ta klasa dostarcza metody do obsługi jednolitego transferu danych i zarządzania połączeniami.|atlctl.h|
|[IDispatchImpl](../../atl/reference/idispatchimpl-class.md)|Ta klasa udostępnia domyślną implementację interfejsu dla `IDispatch` część podwójnego interfejsu.|atlcom.h|
|[Z interfejsu IDispEventImpl](../../atl/reference/idispeventimpl-class.md)|Ta klasa zawiera implementacje `IDispatch` metody.|atlcom.h|
|[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)|Ta klasa zawiera implementacje `IDispatch` metody bez pobierania informacji o typie z biblioteki typów.|atlcom.h|
|[IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md)|Interfejs do analizowania Microsoft HTML i aparat renderowania.|atlbase.h, ATLIFace.h|
|[IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)|Ta klasa definiuje interfejs moduł wyliczający na podstawie kolekcji standardowej biblioteki języka C++.|atlcom.h|
|[IObjectSafetyImpl](../../atl/reference/iobjectsafetyimpl-class.md)|Ta klasa udostępnia domyślną implementację elementu `IObjectSafety` interfejsu, aby umożliwić klientowi pobierać i ustawiać poziom bezpieczeństwa obiektu.|atlctl.h|
|[IObjectWithSiteImpl](../../atl/reference/iobjectwithsiteimpl-class.md)|Ta klasa dostarcza metody, dzięki czemu obiekt, do komunikacji z jej lokacją.|atlcom.h|
|[IOleControlImpl](../../atl/reference/iolecontrolimpl-class.md)|Ta klasa udostępnia domyślną implementację elementu `IOleControl` interfejsu i implementuje `IUnknown`.|atlctl.h|
|[IOleInPlaceActiveObjectImpl](../../atl/reference/ioleinplaceactiveobjectimpl-class.md)|Ta klasa dostarcza metody obsługi komunikacji między formantem w miejscu, a jego kontenera.|atlctl.h|
|[IOleInPlaceObjectWindowlessImpl](../../atl/reference/ioleinplaceobjectwindowlessimpl-class.md)|Ta klasa implementuje `IUnknown` i dostarcza metod, które umożliwiają kontrolce do odbierania komunikatów okien i uczestniczyć w operacji przeciągania i upuszczania.|atlctl.h|
|[IOleObjectImpl](../../atl/reference/ioleobjectimpl-class.md)|Ta klasa implementuje `IUnknown` i jest główną interfejs, za pomocą którego kontener komunikuje się za pomocą kontrolki.|atlctl.h|
|[IPerPropertyBrowsingImpl](../../atl/reference/iperpropertybrowsingimpl-class.md)|Ta klasa implementuje `IUnknown` i umożliwia klientom dostęp do informacji na stronach właściwości obiektu.|atlctl.h|
|[IPersistPropertyBagImpl](../../atl/reference/ipersistpropertybagimpl-class.md)|Ta klasa implementuje `IUnknown` i zezwala na obiekt zapisać właściwości zbioru właściwości dostarczonych przez klienta.|atlcom.h|
|[IPersistStorageImpl](../../atl/reference/ipersiststorageimpl-class.md)|Ta klasa implementuje [IPersistStorage](/windows/desktop/api/objidl/nn-objidl-ipersiststorage) interfejsu.|atlcom.h|
|[IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md)|Ta klasa implementuje `IUnknown` i udostępnia domyślną implementację elementu [IPersistStreamInit](/windows/desktop/api/ocidl/nn-ocidl-ipersiststreaminit) interfejsu.|atlcom.h|
|[IPointerInactiveImpl](../../atl/reference/ipointerinactiveimpl-class.md)|Ta klasa implementuje `IUnknown` i [IPointerInactive](/windows/desktop/api/ocidl/nn-ocidl-ipointerinactive) metody interfejsu.|atlctl.h|
|[IPropertyNotifySinkCP](../../atl/reference/ipropertynotifysinkcp-class.md)|Ta klasa udostępnia [ipropertynotifysink —](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink) interfejs jako interfejsu wychodzącego w obiekcie składnika.|atlctl.h|
|[IPropertyPage2Impl](../../atl/reference/ipropertypage2impl-class.md)|Ta klasa implementuje `IUnknown` i dziedziczy domyślna Implementacja klasy [IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md).|atlctl.h|
|[IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)|Ta klasa implementuje `IUnknown` i udostępnia domyślną implementację elementu [IPropertyPage](/windows/desktop/api/ocidl/nn-ocidl-ipropertypage) interfejsu.|atlctl.h|
|[IProvideClassInfo2Impl](../../atl/reference/iprovideclassinfo2impl-class.md)|Ta klasa udostępnia domyślną implementację elementu [IProvideClassInfo](/windows/desktop/api/ocidl/nn-ocidl-iprovideclassinfo) i [IProvideClassInfo2](/windows/desktop/api/ocidl/nn-ocidl-iprovideclassinfo2) metody.|atlcom.h|
|[IQuickActivateImpl](../../atl/reference/iquickactivateimpl-class.md)|Ta klasa łączy inicjowania kontroli kontenery w jednym wywołaniu.|atlctl.h|
|[IRunnableObjectImpl](../../atl/reference/irunnableobjectimpl-class.md)|Ta klasa implementuje `IUnknown` i udostępnia domyślną implementację elementu [IRunnableObject](/windows/desktop/api/objidl/nn-objidl-irunnableobject) interfejsu.|atlctl.h|
|[IServiceProviderImpl](../../atl/reference/iserviceproviderimpl-class.md)|Ta klasa udostępnia domyślną implementację elementu `IServiceProvider` interfejsu.|atlcom.h|
|[ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md)|Ta klasa implementuje `IUnknown` i udostępnia domyślną implementację elementu [ISpecifyPropertyPages](/windows/desktop/api/ocidl/nn-ocidl-ispecifypropertypages) interfejsu.|atlcom.h|
|[ISupportErrorInfoImpl](../../atl/reference/isupporterrorinfoimpl-class.md)|Ta klasa udostępnia domyślną implementację elementu `ISupportErrorInfo Interface` interfejsu i mogą być używane, gdy tylko jeden interfejs generuje błędy na obiekcie.|atlcom.h|
|[Interfejs IThreadPoolConfig](../../atl/reference/ithreadpoolconfig-interface.md)|Ten interfejs zapewnia metody konfigurowania puli wątków.|atlutil.h|
|[IViewObjectExImpl](../../atl/reference/iviewobjecteximpl-class.md)|Ta klasa implementuje `IUnknown` i zawiera domyślne implementacje [IViewObject](/windows/desktop/api/oleidl/nn-oleidl-iviewobject), [IViewObject2](/windows/desktop/api/oleidl/nn-oleidl-iviewobject2), i [IViewObjectEx](/windows/desktop/api/ocidl/nn-ocidl-iviewobjectex) interfejsów.|atlctl.h|
|[Interfejs IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md)|`IWorkerThreadClient` interfejs implementowany przez klientów [CWorkerThread](../../atl/reference/cworkerthread-class.md) klasy.|atlutil.h|
|[_U_MENUorID](../../atl/reference/u-menuorid-class.md)|Ta klasa udostępnia otokę dla `CreateWindow` i `CreateWindowEx`.|atlwin.h|
|[_U_RECT](../../atl/reference/u-rect-class.md)|Ta klasa adaptera argument umożliwia albo `RECT` wskaźników lub odwołań, które zostaną przekazane do funkcji, która jest zaimplementowana w zakresie wskaźników.|atlwin.h|
|[_U_STRINGorID](../../atl/reference/u-stringorid-class.md)|Ta klasa adaptera argument umożliwia nazw zasobów (LPCTSTRs) lub identyfikatory zasobów (UINTs), który zostanie przekazany do funkcji bez konieczności obiekt wywołujący, aby przekonwertować na ciąg przy użyciu makra MAKEINTRESOURCE identyfikator.|atlwin.h|
|[Win32ThreadTraits](../../atl/reference/win32threadtraits-class.md)|Ta klasa udostępnia funkcję tworzenia wątku Windows. Jeśli wątek nie użyje funkcji CRT, należy użyć tej klasy.|atlbase.h|

## <a name="see-also"></a>Zobacz także

[Składniki ATL COM pulpitu](../../atl/atl-com-desktop-components.md)<br/>
[Funkcje](../../atl/reference/atl-functions.md)<br/>
[Zmienne globalne](../../atl/reference/atl-global-variables.md)<br/>
[Typedefs](../../atl/reference/atl-typedefs.md)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
