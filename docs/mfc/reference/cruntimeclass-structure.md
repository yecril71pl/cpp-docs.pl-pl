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
ms.openlocfilehash: c7a7b0f8c61226260497baced9575c911b425512
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50078781"
---
# <a name="cruntimeclass-structure"></a>Struktura CRuntimeClass

Każda klasa jest pochodną `CObject` jest skojarzony z `CRuntimeClass` strukturę, która służy do uzyskania informacji na temat swojej klasy bazowej lub obiektu w czasie wykonywania.

## <a name="syntax"></a>Składnia

```
struct CRuntimeClass
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CRuntimeClass::CreateObject](#createobject)|Tworzy obiekt w czasie wykonywania.|
|[CRuntimeClass::FromName](#fromname)|Tworzy obiekt w czasie wykonywania przy użyciu nazwy klasy znanych.|
|[CRuntimeClass::IsDerivedFrom](#isderivedfrom)|Określa, jeśli klasa jest tworzony na podstawie określonej klasy.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CRuntimeClass::m_lpszClassName](#m_lpszclassname)|Nazwa klasy.|
|[CRuntimeClass::m_nObjectSize](#m_nobjectsize)|Rozmiar obiektu w bajtach.|
|[CRuntimeClass::m_pBaseClass](#m_pbaseclass)|Wskaźnik do `CRuntimeClass` strukturę klasy bazowej.|
|[CRuntimeClass::m_pfnCreateObject](#m_pfncreateobject)|Wskaźnik funkcji, które dynamicznie tworzy obiekt.|
|[CRuntimeClass::m_pfnGetBaseClass](#m_pfngetbaseclass)|Zwraca `CRuntimeClass` struktury (tylko dostępne w przypadku dynamicznie połączone).|
|[CRuntimeClass::m_wSchema](#m_wschema)|Liczba schematu klasy.|

## <a name="remarks"></a>Uwagi

`CRuntimeClass` jest to struktura i dlatego nie ma klasy bazowej.

Możliwość określenia klasy obiektu w czasie wykonywania jest przydatne, gdy są potrzebne dodatkowe sprawdzanie argumenty funkcji typu lub należy napisać kod specjalnych, na podstawie klasy obiektu. Informacje o klasie czasu wykonywania nie jest obsługiwana bezpośrednio za pomocą języka C++.

`CRuntimeClass` zawiera informacje na temat powiązanych obiektu języka C++, takie jak wskaźnik do `CRuntimeClass` klasy bazowej i nazwa klasy ASCII klasy pokrewne. Ta struktura implementuje również różne funkcje, które umożliwiają dynamiczne tworzenie obiektów, określając typ obiektu, używając przyjaznej nazwy i określanie, jeśli klasa powiązane jest tworzony na podstawie określonej klasy.

Aby uzyskać więcej informacji na temat korzystania z `CRuntimeClass`, zapoznaj się z artykułem [uzyskiwania dostępu do środowiska wykonawczego informacji o klasie](../../mfc/accessing-run-time-class-information.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CRuntimeClass`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

##  <a name="createobject"></a>  CRuntimeClass::CreateObject

Wywołaj tę funkcję, umożliwia dynamiczne tworzenie określonej klasy w czasie wykonywania.

```
CObject* CreateObject();

static CObject* PASCAL CreateObject(LPCSTR lpszClassName);

static CObject* PASCAL CreateObject(LPCWSTR lpszClassName);
```

### <a name="parameters"></a>Parametry

*lpszClassName*<br/>
Przyjaznej nazwy klasy, która ma zostać utworzony.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do nowo utworzony obiekt lub wartość NULL, jeśli nazwa klasy nie zostanie znaleziony, lub za mało pamięci do utworzenia obiektu.

### <a name="remarks"></a>Uwagi

Klasy pochodne `CObject` może obsługiwać dynamiczne tworzenie, który jest możliwość tworzenia obiekt określonej klasy w czasie wykonywania. Klasy ramki, dokumentów i wyświetlanie na przykład, powinien obsługiwać dynamiczne tworzenie. Aby uzyskać więcej informacji na temat tworzenia dynamicznego i `CreateObject` elementu członkowskiego, zobacz [klasa CObject](../../mfc/using-cobject.md) i [klasa CObject: Określanie poziomów funkcjonalności](../../mfc/specifying-levels-of-functionality.md).

### <a name="example"></a>Przykład

  Zobacz przykład [IsDerivedFrom](#isderivedfrom).

##  <a name="fromname"></a>  CRuntimeClass::FromName

Wywołaj tę funkcję, aby pobrać `CRuntimeClass` struktury skojarzone z przyjaznej nazwy.

```
static CRuntimeClass* PASCAL FromName(LPCSTR lpszClassName);

static CRuntimeClass* PASCAL FromName(LPCWSTR lpszClassName);
```

### <a name="parameters"></a>Parametry

*lpszClassName*<br/>
Przyjaznej nazwy klasy pochodne `CObject`.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CRuntimeClass` obiektu odpowiadającej nazwie jako zakończony powodzeniem w *lpszClassName*. Funkcja zwraca wartość NULL, jeśli znaleziono nie pasujących nazwy klasy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCObjectSample#17](../../mfc/codesnippet/cpp/cruntimeclass-structure_1.cpp)]

##  <a name="isderivedfrom"></a>  CRuntimeClass::IsDerivedFrom

Wywołaj tę funkcję, aby określić, jeśli wywołujący klasa pochodzi od klasy określonej w *pBaseClass* parametru.

```
BOOL IsDerivedFrom(const CRuntimeClass* pBaseClass) const;

```

### <a name="parameters"></a>Parametry

*pBaseClass*<br/>
Przyjaznej nazwy klasy pochodne `CObject`.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli wywołanie klasy `IsDerivedFrom` pochodzą od podstawy klasy, których `CRuntimeClass` struktura jest dany jako parametru; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Relacja jest określany przez "zjawisku"analizowania z elementu członkowskiego klasy łańcuch klas pochodnych do góry. Ta funkcja tylko zwraca wartość FALSE, jeśli nie zostanie znalezione dopasowanie dla klasy podstawowej.

> [!NOTE]
>  Aby użyć `CRuntimeClass` struktury, należy dołączyć IMPLEMENT_DYNAMIC IMPLEMENT_DYNCREATE i IMPLEMENT_SERIAL — makro implementację klasy, dla którego chcesz pobrać informacji o obiekcie środowiska wykonawczego.

Aby uzyskać więcej informacji na temat korzystania z `CRuntimeClass`, zapoznaj się z artykułem [klasa CObject: uzyskiwanie dostępu do środowiska wykonawczego informacji o klasie](../../mfc/accessing-run-time-class-information.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCObjectSample#18](../../mfc/codesnippet/cpp/cruntimeclass-structure_2.cpp)]

##  <a name="m_lpszclassname"></a>  CRuntimeClass::m_lpszClassName

Ciąg zakończony wartością null zawierający nazwę klasy ASCII.

### <a name="remarks"></a>Uwagi

Ta nazwa może służyć do utworzenia wystąpienia klasy przy użyciu `FromName` funkcja elementu członkowskiego.

### <a name="example"></a>Przykład

  Zobacz przykład [IsDerivedFrom](#isderivedfrom).

##  <a name="m_nobjectsize"></a>  CRuntimeClass::m_nObjectSize

Rozmiar obiektu w bajtach.

### <a name="remarks"></a>Uwagi

Jeśli obiekt ma elementy członkowskie danych prowadzące do alokacji pamięci, rozmiar pamięci nie jest dołączony.

### <a name="example"></a>Przykład

  Zobacz przykład [IsDerivedFrom](#isderivedfrom).

##  <a name="m_pbaseclass"></a>  CRuntimeClass::m_pBaseClass

Jeśli aplikacja statycznie łączy się MFC, ten element członkowski danych zawiera wskaźnik do `CRuntimeClass` strukturę klasy bazowej.

### <a name="remarks"></a>Uwagi

Jeśli aplikacja łączy dynamicznie do biblioteki MFC, zobacz [m_pfnGetBaseClass](#m_pfngetbaseclass).

### <a name="example"></a>Przykład

  Zobacz przykład [IsDerivedFrom](#isderivedfrom).

##  <a name="m_pfncreateobject"></a>  CRuntimeClass::m_pfnCreateObject

Wskaźnik funkcji do domyślnego konstruktora, który utworzył obiekt klasy.

### <a name="remarks"></a>Uwagi

This, wskaźnik jest prawidłowa, jeśli klasa obsługuje tworzenie dynamicznej; w przeciwnym razie funkcja zwraca wartość NULL.

##  <a name="m_pfngetbaseclass"></a>  CRuntimeClass::m_pfnGetBaseClass

Jeśli aplikacja używa biblioteki MFC jako współdzieloną DLL, ten element członkowski danych wskazuje funkcję, która zwraca `CRuntimeClass` strukturę klasy bazowej.

### <a name="remarks"></a>Uwagi

Jeśli aplikacja statycznie łączy do biblioteki MFC, zobacz [m_pBaseClass](#m_pbaseclass).

### <a name="example"></a>Przykład

  Zobacz przykład [IsDerivedFrom](#isderivedfrom).

##  <a name="m_wschema"></a>  CRuntimeClass::m_wSchema

Liczba schematu (-1 dla klas nonserializable).

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na liczbach schematu, zobacz [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) makra.

### <a name="example"></a>Przykład

  Zobacz przykład [IsDerivedFrom](#isderivedfrom).

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[CObject::GetRuntimeClass](../../mfc/reference/cobject-class.md#getruntimeclass)<br/>
[CObject::IsKindOf](../../mfc/reference/cobject-class.md#iskindof)<br/>
[RUNTIME_CLASS](run-time-object-model-services.md#runtime_class)<br/>
[IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic)<br/>
[IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dyncreate)<br/>
[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)

