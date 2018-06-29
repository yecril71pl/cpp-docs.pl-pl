---
title: Struktura CRuntimeClass | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CRuntimeClass
dev_langs:
- C++
helpviewer_keywords:
- CRuntimeClass structure [MFC]
- dynamic class information [MFC]
- runtime [MFC], class information
- run-time class [MFC], CRuntimeClass structure
ms.assetid: de62b6ef-90d4-420f-8c70-f58b36976a2b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e36baac5850942239bc9e553ed041a2914f8d670
ms.sourcegitcommit: be0e3457f2884551f18e183ef0ea65c3ded7f689
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2018
ms.locfileid: "37079547"
---
# <a name="cruntimeclass-structure"></a>Struktura CRuntimeClass
Każda klasa pochodzi od `CObject` jest skojarzony z `CRuntimeClass` strukturę, która służy do wyświetlania informacji na temat obiektu lub jej klasa podstawowa w czasie wykonywania.  
  
## <a name="syntax"></a>Składnia  
  
```  
struct CRuntimeClass  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CRuntimeClass::CreateObject](#createobject)|Tworzy obiekt w czasie wykonywania.|  
|[CRuntimeClass::FromName](#fromname)|Tworzy obiekt w czasie wykonywania za pomocą nazwy klasy znane.|  
|[CRuntimeClass::IsDerivedFrom](#isderivedfrom)|Określa, czy klasa pochodzi od określonej klasy.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CRuntimeClass::m_lpszClassName](#m_lpszclassname)|Nazwa klasy.|  
|[CRuntimeClass::m_nObjectSize](#m_nobjectsize)|Rozmiar obiektu w bajtach.|  
|[CRuntimeClass::m_pBaseClass](#m_pbaseclass)|Wskaźnik do `CRuntimeClass` struktury klasy podstawowej.|  
|[CRuntimeClass::m_pfnCreateObject](#m_pfncreateobject)|Wskaźnik do funkcji, która tworzy dynamicznie obiektu.|  
|[CRuntimeClass::m_pfnGetBaseClass](#m_pfngetbaseclass)|Zwraca `CRuntimeClass` struktury (tylko dostępne, gdy dynamicznie połączone).|  
|[CRuntimeClass::m_wSchema](#m_wschema)|Numer schematu klasy.|  
  
## <a name="remarks"></a>Uwagi  
 `CRuntimeClass` jest to struktura i dlatego nie ma klasy podstawowej.  
  
 Możliwość określenia klasy obiektów zawartych w czasie wykonywania jest przydatne, gdy wymagany jest typ dodatkowe sprawdzanie argumentów funkcji, lub gdy musisz napisać kod specjalnych oparty na klasie obiektu. Informacje o klasie czasu wykonywania nie jest obsługiwana bezpośrednio za pomocą języka C++.  
  
 `CRuntimeClass` zawiera informacje na temat powiązanego obiektu języka C++, takie jak wskaźnik do `CRuntimeClass` klasy podstawowej i nazwę klasy ASCII klasy pokrewne. Ta struktura implementuje również różne funkcje, które mogą służyć do dynamicznego tworzenia obiektów określenie typu obiektu przez przy użyciu przyjaznej nazwy, a także określenie, czy powiązane klasa pochodzi od określonej klasy.  
  
 Aby uzyskać więcej informacji na temat używania `CRuntimeClass`, zapoznaj się z artykułem [podczas uzyskiwania dostępu do środowiska wykonawczego informacje o klasie](../../mfc/accessing-run-time-class-information.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `CRuntimeClass`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afx.h  
  
##  <a name="createobject"></a>  CRuntimeClass::CreateObject  
 Wywołanie tej funkcji można dynamicznie utworzyć określonej klasy w czasie wykonywania.  
  
```  
CObject* CreateObject();  
  
static CObject* PASCAL CreateObject(LPCSTR lpszClassName);  
  
static CObject* PASCAL CreateObject(LPCWSTR lpszClassName);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszClassName*  
 Przyjaznej nazwy klasy, która ma być utworzony.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do nowo utworzony obiekt lub **NULL** nie znaleziono nazwy klasy lub za mało pamięci do utworzenia obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Klasy wyprowadzone z `CObject` obsługuje tworzenie dynamicznej, który jest możliwość tworzenia obiekt klasy określonej w czasie wykonywania. Klasy ramki, dokumentów i widoku na przykład powinien obsługiwać tworzenie dynamiczne. Aby uzyskać więcej informacji na temat tworzenia dynamicznego i `CreateObject` — członek, zobacz [CObject — klasa](../../mfc/using-cobject.md) i [klasa CObject: Określanie poziomów funkcjonalności](../../mfc/specifying-levels-of-functionality.md).  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [IsDerivedFrom](#isderivedfrom).  
  
##  <a name="fromname"></a>  CRuntimeClass::FromName  
 Wywołanie tej funkcji można pobrać `CRuntimeClass` struktury skojarzone z przyjaznej nazwy.  
  
```  
static CRuntimeClass* PASCAL FromName(LPCSTR lpszClassName);  
  
static CRuntimeClass* PASCAL FromName(LPCWSTR lpszClassName);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszClassName*  
 Przyjaznej nazwy klasy pochodne `CObject`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do `CRuntimeClass` obiektu odpowiadającej nazwie, jak przekazano *lpszClassName*. Funkcja zwraca **NULL** Jeśli znaleziono nie zgodnych nazwę klasy.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCObjectSample#17](../../mfc/codesnippet/cpp/cruntimeclass-structure_1.cpp)]  
  
##  <a name="isderivedfrom"></a>  CRuntimeClass::IsDerivedFrom  
 Wywołanie tej funkcji, aby określić, czy wywołanie klasa pochodzi z klasy określonej w *pBaseClass* parametru.  
  
```  
BOOL IsDerivedFrom(const CRuntimeClass* pBaseClass) const;

 
```  
  
### <a name="parameters"></a>Parametry  
 *pBaseClass*  
 Przyjaznej nazwy klasy pochodne `CObject`.  
  
### <a name="return-value"></a>Wartość zwracana  
 **Wartość TRUE,** Jeśli wywołaniem klasy `IsDerivedFrom` pochodzi od podstawy klasy, których `CRuntimeClass` struktura jest podany jako parametr, a w przeciwnym **FALSE**.  
  
### <a name="remarks"></a>Uwagi  
 Relacja jest określona przez "przejście" z elementu członkowskiego klasy zapasowej łańcucha klas pochodnych aż do góry. Ta funkcja zwraca tylko **FALSE** Jeżeli nie znaleziono klasy podstawowej.  
  
> [!NOTE]
>  Aby użyć `CRuntimeClass` struktury, musi zawierać implement_dynamic —, implement_dyncreate — lub implement_serial — makro w implementacji klasy, dla którego chcesz pobrać informacji o obiekcie czasu wykonywania.  
  
 Aby uzyskać więcej informacji na temat używania `CRuntimeClass`, zapoznaj się z artykułem [klasa CObject: uzyskiwanie dostępu do środowiska wykonawczego informacje o klasie](../../mfc/accessing-run-time-class-information.md).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCObjectSample#18](../../mfc/codesnippet/cpp/cruntimeclass-structure_2.cpp)]  
  
##  <a name="m_lpszclassname"></a>  CRuntimeClass::m_lpszClassName  
 Zerem ciągu zawierającego nazwę klasy ASCII.  
  
### <a name="remarks"></a>Uwagi  
 Ta nazwa może być używana do utworzenia wystąpienia klasy przy użyciu `FromName` funkcję elementu członkowskiego.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [IsDerivedFrom](#isderivedfrom).  
  
##  <a name="m_nobjectsize"></a>  CRuntimeClass::m_nObjectSize  
 Rozmiar obiektu w bajtach.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli obiekt ma elementy członkowskie danych prowadzące do alokacji pamięci, rozmiar pamięci nie jest dołączony.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [IsDerivedFrom](#isderivedfrom).  
  
##  <a name="m_pbaseclass"></a>  CRuntimeClass::m_pBaseClass  
 Jeśli aplikacja łączy statycznie z MFC, ten element członkowski danych zawiera wskaźnik do `CRuntimeClass` struktury klasy podstawowej.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli aplikacja łączy dynamicznie do biblioteki MFC, zobacz [m_pfnGetBaseClass](#m_pfngetbaseclass).  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [IsDerivedFrom](#isderivedfrom).  
  
##  <a name="m_pfncreateobject"></a>  CRuntimeClass::m_pfnCreateObject  
 Wskaźnik funkcji do domyślnego konstruktora, który utworzył obiekt klasy.  
  
### <a name="remarks"></a>Uwagi  
 Wskaźnik jest nieprawidłowy, jeśli klasa obsługuje tworzenie dynamicznej; w przeciwnym razie funkcja zwraca **NULL**.  
  
##  <a name="m_pfngetbaseclass"></a>  CRuntimeClass::m_pfnGetBaseClass  
 Jeśli aplikacja używa biblioteki MFC jako udostępniony plik DLL, ten element członkowski danych wskazuje funkcja, która zwraca `CRuntimeClass` struktury klasy podstawowej.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli aplikacja łączy statycznie do biblioteki MFC, zobacz [m_pBaseClass](#m_pbaseclass).  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [IsDerivedFrom](#isderivedfrom).  
  
##  <a name="m_wschema"></a>  CRuntimeClass::m_wSchema  
 Numer schematu (-1 dla klas nonserializable).  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na numery schematu, zobacz [implement_serial —](run-time-object-model-services.md#implement_serial) makra.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [IsDerivedFrom](#isderivedfrom).  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [CObject::GetRuntimeClass](../../mfc/reference/cobject-class.md#getruntimeclass)   
 [CObject::IsKindOf](../../mfc/reference/cobject-class.md#iskindof)   
 [RUNTIME_CLASS —](run-time-object-model-services.md#runtime_class)   
 [IMPLEMENT_DYNAMIC —](run-time-object-model-services.md#implement_dynamic)   
 [IMPLEMENT_DYNCREATE —](run-time-object-model-services.md#implement_dyncreate)   
 [IMPLEMENT_SERIAL —](run-time-object-model-services.md#implement_serial)



