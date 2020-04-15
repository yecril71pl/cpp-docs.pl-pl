---
title: Struktura CRuntimeClass
ms.date: 11/04/2016
f1_keywords:
- CRuntimeClass
helpviewer_keywords:
- CRuntimeClass structure [MFC]
- dynamic class information [MFC]
- runtime [MFC], class information
- run-time class [MFC], CRuntimeClass structure
ms.assetid: de62b6ef-90d4-420f-8c70-f58b36976a2b
ms.openlocfilehash: a58b9c97d5683423a0f81f6b5424f19f987943bf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318551"
---
# <a name="cruntimeclass-structure"></a>Struktura CRuntimeClass

Każda klasa pochodząca z `CObject` jest `CRuntimeClass` skojarzony ze strukturą, która służy do uzyskiwania informacji o obiekcie lub jego klasy podstawowej w czasie wykonywania.

## <a name="syntax"></a>Składnia

```
struct CRuntimeClass
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CRuntimeClass::CreateObject](#createobject)|Tworzy obiekt w czasie wykonywania.|
|[CRuntimeClass::FromName](#fromname)|Tworzy obiekt w czasie wykonywania przy użyciu znanej nazwy klasy.|
|[CRuntimeClass::IsDerivedFrom](#isderivedfrom)|Określa, czy klasa jest pochodną określonej klasy.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CRuntimeClass::m_lpszClassName](#m_lpszclassname)|Nazwa klasy.|
|[CRuntimeClass::m_nObjectSize](#m_nobjectsize)|Rozmiar obiektu w bajtach.|
|[CRuntimeClass::m_pBaseClass](#m_pbaseclass)|Wskaźnik do `CRuntimeClass` struktury klasy podstawowej.|
|[CRuntimeClass::m_pfnCreateObject](#m_pfncreateobject)|Wskaźnik do funkcji, która dynamicznie tworzy obiekt.|
|[CRuntimeClass::m_pfnGetBaseClass](#m_pfngetbaseclass)|Zwraca `CRuntimeClass` strukturę (dostępną tylko wtedy, gdy jest połączona dynamicznie).|
|[CRuntimeClass::m_wSchema](#m_wschema)|Numer schematu klasy.|

## <a name="remarks"></a>Uwagi

`CRuntimeClass`jest strukturą i dlatego nie ma klasy podstawowej.

Możliwość określenia klasy obiektu w czasie wykonywania jest przydatna, gdy potrzebne jest sprawdzanie dodatkowych typów argumentów funkcji lub gdy należy napisać kod specjalnego przeznaczenia na podstawie klasy obiektu. Informacje o klasie w czasie wykonywania nie jest obsługiwany bezpośrednio przez język C++.

`CRuntimeClass`zawiera informacje na temat powiązanego obiektu C++, takie jak wskaźnik do klasy `CRuntimeClass` podstawowej i nazwę klasy ASCII powiązanej klasy. Ta struktura implementuje również różne funkcje, które mogą być używane do dynamicznego tworzenia obiektów, określając typ obiektu przy użyciu znanej nazwy i określając, czy klasa pokrewna pochodzi od określonej klasy.

Aby uzyskać więcej `CRuntimeClass`informacji na temat korzystania z programu , zobacz artykuł [Uzyskiwanie dostępu do informacji o klasie w czasie wykonywania](../../mfc/accessing-run-time-class-information.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CRuntimeClass`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

## <a name="cruntimeclasscreateobject"></a><a name="createobject"></a>CRuntimeClass::CreateObject

Wywołanie tej funkcji dynamicznie utworzyć określoną klasę w czasie wykonywania.

```
CObject* CreateObject();

static CObject* PASCAL CreateObject(LPCSTR lpszClassName);

static CObject* PASCAL CreateObject(LPCWSTR lpszClassName);
```

### <a name="parameters"></a>Parametry

*lpszClassName (nazwa klasy)*<br/>
Znana nazwa klasy, która ma zostać utworzona.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do nowo utworzonego obiektu lub NULL, jeśli nazwa klasy nie zostanie znaleziona lub nie ma wystarczającej ilości pamięci do utworzenia obiektu.

### <a name="remarks"></a>Uwagi

Klasy uzyskane `CObject` z może obsługiwać dynamiczne tworzenie, który jest możliwość tworzenia obiektu określonej klasy w czasie wykonywania. Na przykład klasy dokumentu, widoku i ramki powinny obsługiwać tworzenie dynamiczne. Aby uzyskać więcej informacji `CreateObject` na temat tworzenia dynamicznego i elementu członkowskiego, zobacz [CObject Class](../../mfc/using-cobject.md) i [CObject Class: Określając poziomy funkcjonalności](../../mfc/specifying-levels-of-functionality.md).

### <a name="example"></a>Przykład

  Zobacz przykład [isderivedFrom](#isderivedfrom).

## <a name="cruntimeclassfromname"></a><a name="fromname"></a>CRuntimeClass::FromName

Wywołanie tej funkcji, `CRuntimeClass` aby pobrać strukturę skojarzoną ze znaną nazwą.

```
static CRuntimeClass* PASCAL FromName(LPCSTR lpszClassName);

static CRuntimeClass* PASCAL FromName(LPCWSTR lpszClassName);
```

### <a name="parameters"></a>Parametry

*lpszClassName (nazwa klasy)*<br/>
Znana nazwa klasy pochodząca `CObject`od .

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CRuntimeClass` obiektu, odpowiadający nazwie przekazanej w *lpszClassName*. Funkcja zwraca wartość NULL, jeśli nie znaleziono pasującej nazwy klasy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCObjectSample#17](../../mfc/codesnippet/cpp/cruntimeclass-structure_1.cpp)]

## <a name="cruntimeclassisderivedfrom"></a><a name="isderivedfrom"></a>CRuntimeClass::IsDerivedFrom

Wywołanie tej funkcji, aby ustalić, czy klasa wywołująca pochodzi od klasy określonej w parametrze *pBaseClass.*

```
BOOL IsDerivedFrom(const CRuntimeClass* pBaseClass) const;
```

### <a name="parameters"></a>Parametry

*pBaseClass (klasa bazowa)*<br/>
Znana nazwa klasy pochodząca `CObject`od .

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli `IsDerivedFrom` wywołanie klasy pochodzi od `CRuntimeClass` klasy podstawowej, której struktura jest podana jako parametr; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Relacja jest określana przez "chodzenie" z klasy członka w górę łańcucha klas pochodnych aż do góry. Ta funkcja zwraca wartość FAŁSZ tylko wtedy, gdy nie znaleziono dopasowania dla klasy podstawowej.

> [!NOTE]
> Aby użyć `CRuntimeClass` struktury, należy uwzględnić makro IMPLEMENT_DYNAMIC, IMPLEMENT_DYNCREATE lub IMPLEMENT_SERIAL w implementacji klasy, dla której mają być pobierane informacje o obiekcie w czasie wykonywania.

Aby uzyskać więcej `CRuntimeClass`informacji na temat używania , zobacz artykuł [CObject Klasa: Uzyskiwanie dostępu do informacji o klasie w czasie wykonywania](../../mfc/accessing-run-time-class-information.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCObjectSample#18](../../mfc/codesnippet/cpp/cruntimeclass-structure_2.cpp)]

## <a name="cruntimeclassm_lpszclassname"></a><a name="m_lpszclassname"></a>CRuntimeClass::m_lpszClassName

Ciąg zakończony z wartością null zawierający nazwę klasy ASCII.

### <a name="remarks"></a>Uwagi

Ta nazwa może służyć do tworzenia wystąpienia `FromName` klasy przy użyciu funkcji elementu członkowskiego.

### <a name="example"></a>Przykład

  Zobacz przykład [isderivedFrom](#isderivedfrom).

## <a name="cruntimeclassm_nobjectsize"></a><a name="m_nobjectsize"></a>CRuntimeClass::m_nObjectSize

Rozmiar obiektu w bajtach.

### <a name="remarks"></a>Uwagi

Jeśli obiekt ma elementy członkowskie danych, które wskazują na przydzieloną pamięć, rozmiar tej pamięci nie jest uwzględniony.

### <a name="example"></a>Przykład

  Zobacz przykład [isderivedFrom](#isderivedfrom).

## <a name="cruntimeclassm_pbaseclass"></a><a name="m_pbaseclass"></a>CRuntimeClass::m_pBaseClass

Jeśli aplikacja statycznie łączy się z MFC, ten `CRuntimeClass` element członkowski danych zawiera wskaźnik do struktury klasy podstawowej.

### <a name="remarks"></a>Uwagi

Jeśli aplikacja dynamicznie łączy się z biblioteką MFC, zobacz [m_pfnGetBaseClass](#m_pfngetbaseclass).

### <a name="example"></a>Przykład

  Zobacz przykład [isderivedFrom](#isderivedfrom).

## <a name="cruntimeclassm_pfncreateobject"></a><a name="m_pfncreateobject"></a>CRuntimeClass::m_pfnCreateObject

Wskaźnik funkcji do domyślnego konstruktora, który tworzy obiekt klasy.

### <a name="remarks"></a>Uwagi

Ten wskaźnik jest prawidłowy tylko wtedy, gdy klasa obsługuje dynamiczne tworzenie; w przeciwnym razie funkcja zwraca wartość NULL.

## <a name="cruntimeclassm_pfngetbaseclass"></a><a name="m_pfngetbaseclass"></a>CRuntimeClass::m_pfnGetBaseClass

Jeśli aplikacja używa biblioteki MFC jako udostępnionej biblioteki DLL, ten `CRuntimeClass` element członkowski danych wskazuje na funkcję, która zwraca strukturę klasy podstawowej.

### <a name="remarks"></a>Uwagi

Jeśli aplikacja statycznie łączy się z biblioteką MFC, zobacz [m_pBaseClass](#m_pbaseclass).

### <a name="example"></a>Przykład

  Zobacz przykład [isderivedFrom](#isderivedfrom).

## <a name="cruntimeclassm_wschema"></a><a name="m_wschema"></a>CRuntimeClass::m_wSchema

Numer schematu ( -1 dla klas nienaserializacyjnych).

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat numerów schematów, zobacz [makro IMPLEMENT_SERIAL.](run-time-object-model-services.md#implement_serial)

### <a name="example"></a>Przykład

  Zobacz przykład [isderivedFrom](#isderivedfrom).

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[CObject::GetRuntimeClass](../../mfc/reference/cobject-class.md#getruntimeclass)<br/>
[CObject::IsKindOf](../../mfc/reference/cobject-class.md#iskindof)<br/>
[RUNTIME_CLASS](run-time-object-model-services.md#runtime_class)<br/>
[Implement_dynamic](run-time-object-model-services.md#implement_dynamic)<br/>
[Implement_dyncreate](run-time-object-model-services.md#implement_dyncreate)<br/>
[Implement_serial](run-time-object-model-services.md#implement_serial)
