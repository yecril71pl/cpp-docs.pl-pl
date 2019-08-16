---
title: Klasy i struktury ATL | Microsoft Docs
ms.date: 05/03/2018
helpviewer_keywords:
- classes [C++], ATL
- ATL, classes
ms.assetid: 7da42e2d-ac84-4506-92bd-502a86d68bdc
ms.openlocfilehash: 2bf13700ada3284b8a32718d21971e89e30e5b76
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498049"
---
# <a name="atl-classes-and-structs"></a>Klasy i struktury ATL

Active Template Library (ATL) zawiera następujące klasy i struktury. Aby znaleźć konkretną klasę według kategorii, zobacz [Omówienie klasy ATL](../../atl/atl-class-overview.md).

|Klasa/struktura|Opis|Plik nagłówka|
|-----------|-----------------|-----------------|
|[ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md)|Zawiera informacje służące do renderowania do różnych elementów docelowych, takich jak drukarka, metaplik lub Kontrolka ActiveX.|atlctl. h|
|[_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md)|Zawiera dane wystąpienia klasy w kodzie okna w ATL.|atlbase.h|
|[_ATL_BASE_MODULE70](../../atl/reference/atl-base-module70-structure.md)|Używane przez dowolny projekt, który używa ATL.|atlbase.h|
|[_ATL_COM_MODULE70](../../atl/reference/atl-com-module70-structure.md)|Używany przez kod związany z modelem COM w ATL.| atlbase.h|
|[_ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md)|Zawiera informacje o typie używane do opisywania metody lub właściwości w dispinterface.|atlcom.h|
|[_ATL_MODULE70](../../atl/reference/atl-module70-structure.md)|Zawiera dane używane przez każdy moduł ATL.|atlbase.h|
|[_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md)|Używane przez kod okna w ATL.|atlbase.h|
|[CA2AEX](../../atl/reference/ca2aex-class.md)|Ta klasa jest używana przez makra konwersji ciągów CA2TEX i CT2AEX oraz typedef CA2A.|atlconv. h|
|[CA2CAEX](../../atl/reference/ca2caex-class.md)|Ta klasa jest używana przez makra konwersji ciągów CA2CTEX i CT2CAEX oraz typedef CA2CA.|atlconv. h|
|[CA2WEX](../../atl/reference/ca2wex-class.md)|Ta klasa jest używana przez makra konwersji ciągów CA2TEX, CA2CTEX, CT2WEX i CT2CWEX oraz typedef CA2W.|atlconv. h|
|[CAccessToken](../../atl/reference/caccesstoken-class.md)|Ta klasa jest otoką dla tokenu dostępu.|atlsecurity.h|
|[Cacls](../../atl/reference/cacl-class.md)|Ta klasa jest otoką dla struktury listy kontroli dostępu (ACL).|atlsecurity.h|
|[CAdapt](../../atl/reference/cadapt-class.md)|Ten szablon jest używany do opakowywania klas, które ponownie definiują operator address-of, aby zwrócić coś innego niż adres obiektu.|atlcomcli.h|
|[CAtlArray](../../atl/reference/catlarray-class.md)|Ta klasa implementuje obiekt Array.|atlcoll.h|
|[CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md)|Ta klasa implementuje serwer COM z pulą wątków, model typu Apartment.|atlbase.h|
|[CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md)|Ta klasa zawiera metody implementacji serwera COM w puli wątków, który jest modelem typu Apartment.|atlbase.h|
|[CAtlBaseModule](../../atl/reference/catlbasemodule-class.md)|Ta klasa jest tworzona w każdym projekcie ATL.|atlcore. h|
|[CAtlComModule](../../atl/reference/catlcommodule-class.md)|Ta klasa implementuje moduł serwera COM.|atlbase.h|
|[CAtlDebugInterfacesModule](../../atl/reference/catldebuginterfacesmodule-class.md)|Ta klasa zapewnia obsługę interfejsów debugowania.|atlbase.h|
|[CAtlDllModuleT](../../atl/reference/catldllmodulet-class.md)|Ta klasa reprezentuje moduł biblioteki DLL.|atlbase.h|
|[CAtlException](../../atl/reference/catlexception-class.md)|Ta klasa definiuje wyjątek ATL.|atlexcept.h|
|[CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)|Ta klasa reprezentuje moduł aplikacji.|atlbase.h|
|[CAtlFile](../../atl/reference/catlfile-class.md)|Ta klasa udostępnia cienkią otokę wokół interfejsu API obsługi plików systemu Windows.|atlfile.h|
|[CAtlFileMapping](../../atl/reference/catlfilemapping-class.md)|Ta klasa reprezentuje plik mapowany w pamięci, dodając operator rzutowania do metod [CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md).|atlfile.h|
|[CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)|Ta klasa reprezentuje plik mapowany w pamięci.|atlfile.h|
|[CAtlList](../../atl/reference/catllist-class.md)|Ta klasa udostępnia metody tworzenia obiektu listy i zarządzania nim.|atlcoll.h|
|[CAtlMap](../../atl/reference/catlmap-class.md)|Ta klasa udostępnia metody tworzenia obiektu mapy i zarządzania nim.|atlcoll.h|
|[CAtlModule](../../atl/reference/catlmodule-class.md)|Ta klasa udostępnia metody używane przez kilka klas modułów ATL.|atlbase.h|
|[CAtlModuleT](../../atl/reference/catlmodulet-class.md)|Ta klasa implementuje moduł ATL.|atlbase.h|
|[CAtlPreviewCtrlImpl](../../atl/reference/catlpreviewctrlimpl-class.md)|Ta klasa jest implementacją ATL okna, która jest umieszczana w oknie hosta dostarczonym przez powłokę dla bogatej wersji zapoznawczej.|atlpreviewctrlimpl.h|
|[CAtlServiceModuleT](../../atl/reference/catlservicemodulet-class.md)|Ta klasa implementuje usługę.|atlbase.h|
|[CAtlTemporaryFile](../../atl/reference/catltemporaryfile-class.md)|Ta klasa zawiera metody tworzenia i używania pliku tymczasowego.|atlfile.h|
|[CAtlTransactionManager](../../atl/reference/catltransactionmanager-class.md)|Ta klasa dostarcza otokę do funkcji Menedżera transakcji jądra (KTM).|atltransactionmanager. h|
|[CAtlWinModule](../../atl/reference/catlwinmodule-class.md)|Ta klasa zapewnia obsługę składników okienek ATL.|atlbase.h|
|[CAutoPtr](../../atl/reference/cautoptr-class.md)|Ta klasa reprezentuje obiekt inteligentnego wskaźnika.|atlbase.h|
|[CAutoPtrArray](../../atl/reference/cautoptrarray-class.md)|Ta klasa zapewnia metody przydatne podczas konstruowania tablicy inteligentnych wskaźników.|atlbase.h|
|[CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md)|Ta klasa udostępnia metody, funkcje statyczne i definicje typów przydatne podczas tworzenia kolekcji inteligentnych wskaźników.|atlcoll.h|
|[CAutoPtrList](../../atl/reference/cautoptrlist-class.md)|Ta klasa udostępnia metody przydatne podczas konstruowania listy inteligentnych wskaźników.|atlcoll.h|
|[CAutoVectorPtr](../../atl/reference/cautovectorptr-class.md)|Ta klasa reprezentuje obiekt inteligentnego wskaźnika przy użyciu operatorów New i DELETE Vector.|atlbase.h|
|[CAutoVectorPtrElementTraits](../../atl/reference/cautovectorptrelementtraits-class.md)|Ta klasa udostępnia metody, funkcje statyczne i definicje typów przydatne podczas tworzenia kolekcji inteligentnych wskaźników przy użyciu operatorów New i DELETE Vector.|atlcoll.h|
|[CAxDialogImpl](../../atl/reference/caxdialogimpl-class.md)|Ta klasa implementuje okno dialogowe (modalne lub niemodalne), które obsługuje kontrolki ActiveX.|atlwin.h|
|[CAxWindow](../../atl/reference/caxwindow-class.md)|Ta klasa udostępnia metody manipulowania oknem obsługującym formant ActiveX.|atlwin.h|
|[CAxWindow2T](../../atl/reference/caxwindow2t-class.md)|Ta klasa udostępnia metody manipulowania oknem, które obsługuje kontrolkę ActiveX, a także obsługuje hostowanie kontrolek ActiveX licencjonowanych.|atlwin.h|
|[CBindStatusCallback](../../atl/reference/cbindstatuscallback-class.md)|Ta klasa implementuje `IBindStatusCallback` interfejs.|atlctl. h|
|[CComAggObject](../../atl/reference/ccomaggobject-class.md)|Ta klasa implementuje [interfejs IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) dla obiektu agregowanego.|atlcom.h|
|[CComAllocator](../../atl/reference/ccomallocator-class.md)|Ta klasa udostępnia metody zarządzania pamięcią za pomocą procedur pamięci COM.|atlbase.h|
|[CComApartment](../../atl/reference/ccomapartment-class.md)|Ta klasa zapewnia obsługę zarządzania apartamentem w module programu EXE w puli wątków.|atlbase.h|
|[CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md)|Ta klasa zapewnia metody uzyskiwania i zwalniania własności obiektu sekcji krytycznej.|atlcore. h|
|[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)|Począwszy od biblioteki ATL 7,0 `CComAutoThreadModule` , jest przestarzały: zobacz [moduły ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.|atlbase.h|
|[CComBSTR](../../atl/reference/ccombstr-class.md)|Ta klasa jest otoką dla BSTRs.|atlbase.h|
|[CComCachedTearOffObject](../../atl/reference/ccomcachedtearoffobject-class.md)|Ta klasa implementuje interfejs [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) dla interfejsu odrywanego.|atlcom.h|
|[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)|Ta klasa implementuje interfejs [elementu IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory) .|atlcom.h|
|[CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)|Ta klasa implementuje interfejs [IClassFactory2](/windows/win32/api/ocidl/nn-ocidl-iclassfactory2) .|atlcom.h|
|[CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)|Ta klasa implementuje interfejs [elementu IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory) i umożliwia tworzenie obiektów w wielu apartamentachach.|atlcom.h|
|[CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md)|Ta klasa pochodzi z [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) i używa [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) do konstruowania pojedynczego obiektu.|atlcom.h|
|[CComCoClass](../../atl/reference/ccomcoclass-class.md)|Ta klasa dostarcza metody do tworzenia wystąpień klasy i uzyskiwania jej właściwości.|atlcom.h|
|[CComCompositeControl](../../atl/reference/ccomcompositecontrol-class.md)|Ta klasa dostarcza metody wymagane do zaimplementowania formantu złożonego.|atlctl. h|
|[CComContainedObject](../../atl/reference/ccomcontainedobject-class.md)|Ta klasa implementuje [interfejs IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) przez delegowanie do obiektu `IUnknown`właściciela.|atlcom.h|
|[CComControl](../../atl/reference/ccomcontrol-class.md)|Ta klasa udostępnia metody tworzenia formantów ATL i zarządzania nimi.|atlctl. h|
|[CComControlBase](../../atl/reference/ccomcontrolbase-class.md)|Ta klasa udostępnia metody tworzenia formantów ATL i zarządzania nimi.|atlctl. h|
|[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)|Ta klasa zapewnia metody uzyskiwania i zwalniania własności obiektu sekcji krytycznej.|atlcore. h|
|[CComCritSecLock](../../atl/reference/ccomcritseclock-class.md)|Ta klasa zapewnia metody blokowania i odblokowywania obiektu sekcji krytycznej.|atlbase.h|
|[CComCurrency](../../atl/reference/ccomcurrency-class.md)|Ta klasa ma metody i operatory do tworzenia obiektu waluty i zarządzania nim.|atlcur.h|
|[CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md)|Ta klasa przechowuje tablicę `IUnknown` wskaźników.|atlcom.h|
|[CComEnum](../../atl/reference/ccomenum-class.md)|Ta klasa definiuje obiekt modułu wyliczającego COM w oparciu o tablicę.|atlcom.h|
|[CComEnumImpl](../../atl/reference/ccomenumimpl-class.md)|Ta klasa udostępnia implementację interfejsu modułu wyliczającego COM, w którym wyliczane elementy są przechowywane w tablicy.|atlcom.h|
|[CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md)|Ta klasa definiuje obiekt modułu wyliczającego COM na C++ podstawie standardowej kolekcji biblioteki.|atlcom.h|
|[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)|Ta klasa zawiera te same metody co [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) , ale nie udostępnia sekcji krytycznej.|atlcore. h|
|[CComGITPtr](../../atl/reference/ccomgitptr-class.md)|Ta klasa dostarcza metody do pracy z wskaźnikami interfejsu i globalną tabelą interfejsów (GIT).|atlbase.h|
|[CComHeap](../../atl/reference/ccomheap-class.md)|Ta klasa implementuje [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) przy użyciu funkcji alokacji pamięci com.|ATLComMem.h|
|[CComHeapPtr](../../atl/reference/ccomheapptr-class.md)|Klasa inteligentnego wskaźnika do zarządzania wskaźnikami sterty.|atlbase.h|
|[CComModule](../../atl/reference/ccommodule-class.md)|Począwszy od biblioteki ATL 7,0 `CComModule` , jest przestarzały: zobacz [moduły ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.|atlbase.h|
|[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)|Ta klasa zapewnia bezpieczne dla wątków metody zwiększania i zmniejszania wartości zmiennej.|atlbase.h|
|[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)|Ta klasa zapewnia bezpieczne dla wątków metody zwiększania i zmniejszania wartości zmiennej, bez krytycznego blokowania sekcji lub odblokowywania.|atlbase.h|
|[CComObject](../../atl/reference/ccomobject-class.md)|Ta klasa implementuje `IUnknown` dla niezagregowanego obiektu.|atlcom.h|
|[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)|Ta klasa zarządza liczbą odwołań w module zawierającym `Base` obiekt.|atlcom.h|
|[CComObjectNoLock](../../atl/reference/ccomobjectnolock-class.md)|Ta klasa implementuje `IUnknown` dla niezagregowanego obiektu, ale nie zwiększa liczby blokad modułu w konstruktorze.|atlcom.h|
|[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)|Ten element typedef elementu [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md) jest szablonowana na domyślnym modelu wątkowego serwera.|atlcom.h|
|[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)|Ta klasa dostarcza metody do obsługi zarządzania licznikami odwołań do obiektów zarówno dla obiektów niezagregowanych, jak i agregowanych.|atlcom.h|
|[CComObjectStack](../../atl/reference/ccomobjectstack-class.md)|Ta klasa tworzy tymczasowy obiekt COM i udostępnia go z implementacją `IUnknown`szkieletową.|atlcom.h|
|[CComPolyObject](../../atl/reference/ccompolyobject-class.md)|Ta klasa implementuje `IUnknown` obiekt zagregowany lub niezagregowany.|atlcom.h|
|[CComPtr](../../atl/reference/ccomptr-class.md)|Klasa inteligentnego wskaźnika do zarządzania wskaźnikami interfejsu COM.|atlcomcli.h|
|[CComPtrBase](../../atl/reference/ccomptrbase-class.md)|Ta klasa stanowi podstawę dla klas wskaźników inteligentnych korzystających z procedur pamięci opartych na modelu COM.|atlcomcli.h|
|[CComQIPtr](../../atl/reference/ccomqiptr-class.md)|Klasa inteligentnego wskaźnika do zarządzania wskaźnikami interfejsu COM.|atlcomcli.h|
|[CComQIPtrElementTraits](../../atl/reference/ccomqiptrelementtraits-class.md)|Ta klasa udostępnia metody, funkcje statyczne i definicje typów przydatne podczas tworzenia kolekcji wskaźników interfejsu COM.|atlcoll.h|
|[CComSafeArray](../../atl/reference/ccomsafearray-class.md)|Ta klasa jest otoką dla `SAFEARRAY Data Type` struktury.|atlsafe.h|
|[CComSafeArrayBound](../../atl/reference/ccomsafearraybound-class.md)|Ta klasa jest otoką dla `SAFEARRAYBOUND` struktury.|atlsafe.h|
|[CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md)|Ta klasa zarządza wyborem wątku dla klasy [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).|atlbase.h|
|[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)|Ta klasa zapewnia metody zwiększania i zmniejszania wartości zmiennej.|atlbase.h|
|[CComTearOffObject](../../atl/reference/ccomtearoffobject-class.md)|Ta klasa implementuje interfejs odrywający.|atlcom.h|
|[CComUnkArray](../../atl/reference/ccomunkarray-class.md)|Ta klasa przechowuje `IUnknown` wskaźniki i jest przeznaczona do użycia jako parametr klasy szablonu [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) .|atlcom.h|
|[CComVariant](../../atl/reference/ccomvariant-class.md)|Ta klasa otacza typ VARIANT, dostarczając element członkowski wskazujący typ przechowywanych danych.|atlcomcli.h|
|[CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md)|Ta klasa implementuje okno zawarte w innym obiekcie.|atlwin.h|
|[CCRTAllocator](../../atl/reference/ccrtallocator-class.md)|Ta klasa udostępnia metody zarządzania pamięcią za pomocą procedur pamięci CRT.|atlcore. h|
|[CCRTHeap](../../atl/reference/ccrtheap-class.md)|Ta klasa implementuje [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) przy użyciu funkcji sterty CRT.|atlmem.h|
|[CDacl](../../atl/reference/cdacl-class.md)|Ta klasa jest otoką dla struktury DACL (lista arbitralnej kontroli dostępu).|atlsecurity.h|
|[Klasa CDebugReportHook](../../atl/reference/cdebugreporthook-class.md)|Użyj tej klasy, aby wysyłać raporty debugowania do nazwanego potoku.|atlutil.h|
|[CDefaultCharTraits](../../atl/reference/cdefaultchartraits-class.md)|Ta klasa udostępnia dwie statyczne funkcje do konwertowania znaków między wielkie i małe litery.|atlcoll.h|
|[CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)|Ta klasa zapewnia domyślne funkcje porównywania elementów.|atlcoll.h|
|[CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)|Ta klasa dostarcza domyślne metody i funkcje dla klasy kolekcji.|atlcoll.h|
|[CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)|Ta klasa udostępnia funkcję statyczną do obliczania wartości skrótu.|atlcoll.h|
|[CDialogImpl](../../atl/reference/cdialogimpl-class.md)|Ta klasa udostępnia metody tworzenia modalnych lub niemodalnych okien dialogowych.|atlwin.h|
|[CDynamicChain](../../atl/reference/cdynamicchain-class.md)|Ta klasa udostępnia metody obsługujące dynamiczny łańcuch map komunikatów.|atlwin.h|
|[CElementTraits](../../atl/reference/celementtraits-class.md)|Ta klasa jest używana przez klasy kolekcji do udostępniania metod i funkcji na potrzeby operacji przeniesienia, kopiowania, porównywania i tworzenia skrótów.|atlcoll.h|
|[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)|Ta klasa udostępnia domyślne metody kopiowania i przenoszenia dla klasy kolekcji.|atlcoll.h|
|[CFirePropNotifyEvent](../../atl/reference/cfirepropnotifyevent-class.md)|Ta klasa dostarcza metody powiadamiania ujścia kontenera o zmianach właściwości formantu.|atlctl. h|
|[CGlobalHeap](../../atl/reference/cglobalheap-class.md)|Ta klasa implementuje [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) przy użyciu globalnych funkcji sterty Win32.|atlmem.h|
|[CHandle](../../atl/reference/chandle-class.md)|Ta klasa dostarcza metody do tworzenia i używania obiektu uchwytu.|atlbase.h|
|[CHeapPtr](../../atl/reference/cheapptr-class.md)|Klasa inteligentnego wskaźnika do zarządzania wskaźnikami sterty.|atlcore. h|
|[CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)|Ta klasa stanowi podstawę dla kilku klas wskaźników sterty inteligentnej.|atlcore. h|
|[Klasa CHeapPtrElementTraits](../../atl/reference/cheapptrelementtraits-class.md)|Ta klasa udostępnia metody, funkcje statyczne i definicje typów przydatne podczas tworzenia kolekcji wskaźników sterty.|atlcoll.h|
|[CHeapPtrList](../../atl/reference/cheapptrlist-class.md)|Ta klasa udostępnia metody przydatne podczas konstruowania listy wskaźników sterty.|atlcoll.h|
|[CImage](../../atl-mfc-shared/reference/cimage-class.md)|Zapewnia obsługę ulepszonej mapy bitowej, w tym możliwość ładowania i zapisywania obrazów w formatach JPEG, GIF, BMP i Portable Network Graphics (PNG).|atlimage.h|
|[CInterfaceArray](../../atl/reference/cinterfacearray-class.md)|Ta klasa zapewnia metody przydatne podczas konstruowania tablicy wskaźników interfejsu COM.|atlcoll.h|
|[CInterfaceList](../../atl/reference/cinterfacelist-class.md)|Ta klasa udostępnia metody przydatne podczas konstruowania listy wskaźników interfejsu COM.|atlcoll.h|
|[CLocalHeap](../../atl/reference/clocalheap-class.md)|Ta klasa implementuje [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) przy użyciu funkcji sterty lokalnej Win32.|atlmem.h|
|[CMessageMap](../../atl/reference/cmessagemap-class.md)|Ta klasa umożliwia dostęp do mapowań komunikatów obiektu przez inny obiekt.|atlwin.h|
|[Klasa CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md)|Odbiera żądania z puli wątków i przekazuje je do obiektu procesu roboczego, który jest tworzony i niszczony dla każdego żądania.|atlutil.h|
|[Klasa CNoWorkerThread](../../atl/reference/cnoworkerthread-class.md)|Użyj tej klasy jako argumentu dla `MonitorClass` klas pamięci podręcznej parametru szablonu, jeśli chcesz wyłączyć konserwację dynamicznej pamięci podręcznej.|atlutil.h|
|[Klasa CPathT](../../atl/reference/cpatht-class.md)|Ta klasa reprezentuje ścieżkę.|atlpath.h|
|[CPrimitiveElementTraits](../../atl/reference/cprimitiveelementtraits-class.md)|Ta klasa dostarcza domyślne metody i funkcje dla klasy kolekcji, która składa się z typów danych pierwotnych.|atlcoll.h|
|[CPrivateObjectSecurityDesc](../../atl/reference/cprivateobjectsecuritydesc-class.md)|Ta klasa reprezentuje obiekt deskryptora zabezpieczeń obiektu prywatnego.|atlsecurity.h|
|[CRBMap](../../atl/reference/crbmap-class.md)|Ta klasa reprezentuje strukturę mapowania przy użyciu czarno-czarnego drzewa binarnego.|atlcoll.h|
|[CRBMultiMap](../../atl/reference/crbmultimap-class.md)|Ta klasa reprezentuje strukturę mapowania, która umożliwia skojarzenie poszczególnych kluczy z więcej niż jedną wartością, przy użyciu czarnego drzewa binarnego czerwonego.|atlcoll.h|
|[CRBTree](../../atl/reference/crbtree-class.md)|Ta klasa zawiera metody tworzenia i używania czarnego drzewa.|atlcoll.h|
|[CRegKey](../../atl/reference/cregkey-class.md)|Ta klasa zawiera metody manipulowania wpisami w rejestrze systemowym.|atlbase.h|
|[CRTThreadTraits](../../atl/reference/crtthreadtraits-class.md)|Ta klasa udostępnia funkcję tworzenia dla wątku CRT. Użyj tej klasy, jeśli wątek będzie używać funkcji CRT.|atlbase.h|
|[CSacl](../../atl/reference/csacl-class.md)|Ta klasa jest otoką dla struktury SACL (lista kontroli dostępu do systemu).|atlsecurity.h|
|[CSecurityAttributes](../../atl/reference/csecurityattributes-class.md)|Ta klasa to cienka otoka dla `SECURITY_ATTRIBUTES` struktury.|atlsecurity.h|
|[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)|Ta klasa jest otoką dla `SECURITY_DESCRIPTOR` struktury.|atlsecurity.h|
|[CSid](../../atl/reference/csid-class.md)|Ta klasa jest otoką dla `SID` struktury (identyfikator zabezpieczeń).|atlsecurity.h|
|[CSimpleArray](../../atl/reference/csimplearray-class.md)|Ta klasa udostępnia metody zarządzania prostą tablicą.|atlsimpcoll.h|
|[CSimpleArrayEqualHelper](../../atl/reference/csimplearrayequalhelper-class.md)|Ta klasa jest pomocnikiem dla klasy [CSimpleArray](../../atl/reference/csimplearray-class.md) .|atlsimpcoll.h|
|[CSimpleArrayEqualHelperFalse](../../atl/reference/csimplearrayequalhelperfalse-class.md)|Ta klasa jest pomocnikiem dla klasy [CSimpleArray](../../atl/reference/csimplearray-class.md) .|atlsimpcoll.h|
|[CSimpleDialog](../../atl/reference/csimpledialog-class.md)|Ta klasa implementuje podstawowe modalne okno dialogowe.|atlwin.h|
|[CSimpleMap](../../atl/reference/csimplemap-class.md)|Ta klasa zapewnia obsługę prostej tablicy mapowania.|atlsimpcoll.h|
|[CSimpleMapEqualHelper](../../atl/reference/csimplemapequalhelper-class.md)|Ta klasa jest pomocnikiem dla klasy [CSimpleMap](../../atl/reference/csimplemap-class.md) .|atlsimpcoll.h|
|[CSimpleMapEqualHelperFalse](../../atl/reference/csimplemapequalhelperfalse-class.md)|Ta klasa jest pomocnikiem dla klasy [CSimpleMap](../../atl/reference/csimplemap-class.md) .|atlsimpcoll.h|
|[CSnapInItemImpl](../../atl/reference/csnapinitemimpl-class.md)|Ta klasa dostarcza metody do implementowania obiektu węzła przystawki.|atlsnap.h|
|[CSnapInPropertyPageImpl](../../atl/reference/csnapinpropertypageimpl-class.md)|Ta klasa dostarcza metody do implementowania obiektu strony właściwości przystawki.|atlsnap.h|
|[CStockPropImpl](../../atl/reference/cstockpropimpl-class.md)|Ta klasa udostępnia metody obsługi wartości właściwości podstawowych.|atlctl. h|
|[CStringElementTraits](../../atl/reference/cstringelementtraits-class.md)|Ta klasa udostępnia funkcje statyczne używane przez klasy kolekcji przechowujące `CString` obiekty.|cstringt.h|
|[CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md)|Ta klasa udostępnia funkcje statyczne dotyczące ciągów przechowywanych w obiektach klasy kolekcji. Jest to podobne do [CStringElementTraits](../../atl/reference/cstringelementtraits-class.md), ale wykonuje porównania bez uwzględniania wielkości liter.|atlcoll.h|
|[CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md)|Ta klasa udostępnia funkcje statyczne dotyczące ciągów przechowywanych w obiektach klasy kolekcji. Obiekty ciągów są rozpatrywane jako odwołania.|atlcoll.h|
|[Klasa CThreadPool](../../atl/reference/cthreadpool-class.md)|Ta klasa udostępnia pulę wątków roboczych, które przetwarzają kolejkę elementów roboczych.|atlutil.h|
|[CTokenGroups](../../atl/reference/ctokengroups-class.md)|Ta klasa jest otoką dla `TOKEN_GROUPS` struktury.|atlsecurity.h|
|[CTokenPrivileges](../../atl/reference/ctokenprivileges-class.md)|Ta klasa jest otoką dla `TOKEN_PRIVILEGES` struktury.|atlsecurity.h|
|[Klasa CUrl](../../atl/reference/curl-class.md)|Ta klasa reprezentuje adres URL. Pozwala ona na manipulowanie każdym elementem adresu URL niezależnie od innych, niezależnie od tego, czy jest analizowany istniejący ciąg adresu URL, czy też tworzący ciąg od podstaw.|atlutil.h|
|[CW2AEX](../../atl/reference/cw2aex-class.md)|Ta klasa jest używana przez makra konwersji ciągów CT2AEX, CW2TEX, CW2CTEX i CT2CAEX oraz typedef CW2A.|atlconv. h|
|[CW2CWEX](../../atl/reference/cw2cwex-class.md)|Ta klasa jest używana przez makra konwersji ciągów CW2CTEX i CT2CWEX oraz typedef CW2CW.|atlconv. h|
|[CW2WEX](../../atl/reference/cw2wex-class.md)|Ta klasa jest używana przez makra konwersji ciągów CW2TEX i CT2WEX oraz typedef CW2W.|atlconv. h|
|[CWin32Heap](../../atl/reference/cwin32heap-class.md)|Ta klasa implementuje [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) przy użyciu funkcji alokacji sterty Win32.|atlmem.h|
|[CWindow](../../atl/reference/cwindow-class.md)|Ta klasa udostępnia metody manipulowania oknem.|atlwin.h|
|[CWindowImpl](../../atl/reference/cwindowimpl-class.md)|Ta klasa udostępnia metody tworzenia lub podklasy okna.|atlwin.h|
|[CWinTraits](../../atl/reference/cwintraits-class.md)|Ta klasa udostępnia metodę standaryzacji stylów używanych podczas tworzenia obiektu okna.|atlwin.h|
|[CWinTraitsOR](../../atl/reference/cwintraitsor-class.md)|Ta klasa udostępnia metodę standaryzacji stylów używanych podczas tworzenia obiektu okna.|atlwin.h|
|[CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)|Ta klasa udostępnia metody rejestrowania informacji dla klasy okna.|atlwin.h|
|[Klasa CWorkerThread](../../atl/reference/cworkerthread-class.md)|Ta klasa tworzy wątek roboczy lub używa istniejącego obiektu, czeka na co najmniej jeden obiekt jądra, i wykonuje określoną funkcję klienta po zasygnalizowaniu jednego z uchwytów.|atlutil.h|
|[IAtlAutoThreadModule](../../atl/reference/iatlautothreadmodule-class.md)|Ta klasa reprezentuje interfejs do `CreateInstance` metody.|atlbase.h|
|[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)|Ta klasa reprezentuje interfejs Menedżera pamięci.|atlmem.h|
|[IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md)|Ten interfejs zapewnia metody określania właściwości hostowanej kontrolki lub kontenera.|atlbase. h, ATLIFace. h|
|[IAxWinAmbientDispatchEx](../../atl/reference/iaxwinambientdispatchex-interface.md)|Ten interfejs implementuje dodatkowe właściwości otoczenia dla hostowanej kontrolki.|atlbase. h, ATLIFace. h|
|[IAxWinHostWindow](../../atl/reference/iaxwinhostwindow-interface.md)|Ten interfejs zapewnia metody manipulowania kontrolką i jego obiektem hosta.|atlbase. h, ATLIFace. h|
|[IAxWinHostWindowLic](../../atl/reference/iaxwinhostwindowlic-interface.md)|Ten interfejs zapewnia metody manipulowania licencjonowaną kontrolką i jego obiektem hosta.|atlbase. h, ATLIFace. h|
|[ICollectionOnSTLImpl](../../atl/reference/icollectiononstlimpl-class.md)|Ta klasa udostępnia metody używane przez klasę kolekcji.|atlcom.h|
|[IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md)|Ta klasa implementuje kontener punktu połączenia w celu zarządzania kolekcją obiektów [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) .|atlcom.h|
|[IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)|Ta klasa implementuje punkt połączenia.|atlcom.h|
|[IDataObjectImpl](../../atl/reference/idataobjectimpl-class.md)|Ta klasa udostępnia metody obsługi Uniform Data Transfer i zarządzania połączeniami.|atlctl. h|
|[IDispatchImpl](../../atl/reference/idispatchimpl-class.md)|Ta klasa zawiera domyślną implementację `IDispatch` części podwójnego interfejsu.|atlcom.h|
|[IDispEventImpl](../../atl/reference/idispeventimpl-class.md)|Ta klasa udostępnia implementacje `IDispatch` metod.|atlcom.h|
|[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)|Ta klasa udostępnia implementacje `IDispatch` metod bez uzyskiwania informacji o typie z biblioteki typów.|atlcom.h|
|[IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md)|Interfejs do aparatu analizy i renderowania HTML firmy Microsoft.|atlbase. h, ATLIFace. h|
|[IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)|Ta klasa definiuje interfejs modułu wyliczającego na C++ podstawie standardowej kolekcji biblioteki.|atlcom.h|
|[IObjectSafetyImpl](../../atl/reference/iobjectsafetyimpl-class.md)|Ta klasa udostępnia domyślną implementację `IObjectSafety` interfejsu, aby umożliwić klientowi pobieranie i ustawianie poziomów bezpieczeństwa obiektu.|atlctl. h|
|[IObjectWithSiteImpl](../../atl/reference/iobjectwithsiteimpl-class.md)|Ta klasa udostępnia metody umożliwiające obiektowi komunikowanie się z jego lokacją.|atlcom.h|
|[IOleControlImpl](../../atl/reference/iolecontrolimpl-class.md)|Ta klasa zapewnia domyślną implementację `IOleControl` interfejsu i implementuje. `IUnknown`|atlctl. h|
|[IOleInPlaceActiveObjectImpl](../../atl/reference/ioleinplaceactiveobjectimpl-class.md)|Ta klasa zapewnia metody wspomagania komunikacji między kontrolką miejscową i jej kontenerem.|atlctl. h|
|[IOleInPlaceObjectWindowlessImpl](../../atl/reference/ioleinplaceobjectwindowlessimpl-class.md)|Ta klasa implementuje `IUnknown` i udostępnia metody, które umożliwiają kontrolowanie bezokienkowe odbierania komunikatów okna i uczestnictwo w operacjach przeciągania i upuszczania.|atlctl. h|
|[IOleObjectImpl](../../atl/reference/ioleobjectimpl-class.md)|Ta klasa implementuje `IUnknown` i jest interfejsem głównym, za pomocą którego kontener komunikuje się z kontrolką.|atlctl. h|
|[IPerPropertyBrowsingImpl](../../atl/reference/iperpropertybrowsingimpl-class.md)|Ta klasa implementuje `IUnknown` i umożliwia klientowi dostęp do informacji na stronach właściwości obiektu.|atlctl. h|
|[IPersistPropertyBagImpl](../../atl/reference/ipersistpropertybagimpl-class.md)|Ta klasa implementuje `IUnknown` i umożliwia obiektowi zapisanie jego właściwości w zbiorze właściwości dostarczanym przez klienta.|atlcom.h|
|[IPersistStorageImpl](../../atl/reference/ipersiststorageimpl-class.md)|Ta klasa implementuje interfejs [IPersistStorage](/windows/win32/api/objidl/nn-objidl-ipersiststorage) .|atlcom.h|
|[IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md)|Ta klasa implementuje `IUnknown` i udostępnia domyślną implementację interfejsu [IPersistStreamInit](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit) .|atlcom.h|
|[IPointerInactiveImpl](../../atl/reference/ipointerinactiveimpl-class.md)|Ta klasa implementuje `IUnknown` metody interfejsu [IPointerInactive](/windows/win32/api/ocidl/nn-ocidl-ipointerinactive) .|atlctl. h|
|[IPropertyNotifySinkCP](../../atl/reference/ipropertynotifysinkcp-class.md)|Ta klasa udostępnia interfejs [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) jako interfejs wychodzący w obiekcie połączonym.|atlctl. h|
|[IPropertyPage2Impl](../../atl/reference/ipropertypage2impl-class.md)|Ta klasa implementuje `IUnknown` i dziedziczy domyślną implementację [IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md).|atlctl. h|
|[IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)|Ta klasa implementuje `IUnknown` i udostępnia domyślną implementację interfejsu [IPropertyPage](/windows/win32/api/ocidl/nn-ocidl-ipropertypage) .|atlctl. h|
|[IProvideClassInfo2Impl](../../atl/reference/iprovideclassinfo2impl-class.md)|Ta klasa zawiera domyślną implementację metod [IProvideClassInfo](/windows/win32/api/ocidl/nn-ocidl-iprovideclassinfo) i [IProvideClassInfo2](/windows/win32/api/ocidl/nn-ocidl-iprovideclassinfo2) .|atlcom.h|
|[IQuickActivateImpl](../../atl/reference/iquickactivateimpl-class.md)|Ta klasa łączy inicjalizację kontenera kontenerów z pojedynczym wywołaniem.|atlctl. h|
|[IRunnableObjectImpl](../../atl/reference/irunnableobjectimpl-class.md)|Ta klasa implementuje `IUnknown` i udostępnia domyślną implementację interfejsu [IRunnableObject](/windows/win32/api/objidl/nn-objidl-irunnableobject) .|atlctl. h|
|[IServiceProviderImpl](../../atl/reference/iserviceproviderimpl-class.md)|Ta klasa udostępnia domyślną implementację `IServiceProvider` interfejsu.|atlcom.h|
|[ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md)|Ta klasa implementuje `IUnknown` i udostępnia domyślną implementację interfejsu [ISpecifyPropertyPages](/windows/win32/api/ocidl/nn-ocidl-ispecifypropertypages) .|atlcom.h|
|[ISupportErrorInfoImpl](../../atl/reference/isupporterrorinfoimpl-class.md)|Ta klasa udostępnia domyślną implementację `ISupportErrorInfo Interface` interfejsu i może być używana, gdy tylko jeden interfejs generuje błędy w obiekcie.|atlcom.h|
|[Interfejs IThreadPoolConfig](../../atl/reference/ithreadpoolconfig-interface.md)|Ten interfejs zapewnia metody konfigurowania puli wątków.|atlutil.h|
|[IViewObjectExImpl](../../atl/reference/iviewobjecteximpl-class.md)|Ta klasa implementuje `IUnknown` i udostępnia domyślne implementacje interfejsów [IViewObject](/windows/win32/api/oleidl/nn-oleidl-iviewobject), [IViewObject2](/windows/win32/api/oleidl/nn-oleidl-iviewobject2)i [IViewObjectEx](/windows/win32/api/ocidl/nn-ocidl-iviewobjectex) .|atlctl. h|
|[Interfejs IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md)|`IWorkerThreadClient`jest interfejsem implementowanym przez klientów klasy [CWorkerThread](../../atl/reference/cworkerthread-class.md) .|atlutil.h|
|[_U_MENUorID](../../atl/reference/u-menuorid-class.md)|Ta klasa udostępnia otoki dla `CreateWindow` i `CreateWindowEx`.|atlwin.h|
|[_U_RECT](../../atl/reference/u-rect-class.md)|Klasa adaptera argumentów umożliwia `RECT` przekazywanie wskaźników lub odwołań do funkcji, która jest zaimplementowana w warunkach wskaźników.|atlwin.h|
|[_U_STRINGorID](../../atl/reference/u-stringorid-class.md)|Ta klasa adaptera argumentu umożliwia przekazywanie nazw zasobów (LPCTSTRs) lub identyfikatorów zasobów (UINTs) do funkcji bez konieczności, aby obiekt wywołujący przekonwertował identyfikator na ciąg za pomocą makra MAKEINTRESOURCE.|atlwin.h|
|[Win32ThreadTraits](../../atl/reference/win32threadtraits-class.md)|Ta klasa udostępnia funkcję tworzenia dla wątku systemu Windows. Użyj tej klasy, jeśli wątek nie będzie używać funkcji CRT.|atlbase.h|

## <a name="see-also"></a>Zobacz także

[Składniki ATL COM pulpitu](../../atl/atl-com-desktop-components.md)<br/>
[Funkcje](../../atl/reference/atl-functions.md)<br/>
[Zmienne globalne](../../atl/reference/atl-global-variables.md)<br/>
[Definicje typów](../../atl/reference/atl-typedefs.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
