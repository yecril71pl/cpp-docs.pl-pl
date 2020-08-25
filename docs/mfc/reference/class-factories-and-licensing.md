---
title: Fabryki klas i licencjonowanie
ms.date: 11/04/2016
helpviewer_keywords:
- class factories [MFC], and licensing
ms.assetid: 53c4856a-4062-46db-9f69-dd4339f746b3
ms.openlocfilehash: 939d7156a9bd7bf0778d2ab4a40acb2afe10cf6e
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845929"
---
# <a name="class-factories-and-licensing"></a>Fabryki klas i licencjonowanie

Aby utworzyć wystąpienie formantu OLE, aplikacja kontenera wywołuje funkcję członkowską fabryki klas formantu. Ponieważ kontrolka jest rzeczywistym obiektem OLE, fabryka klas jest odpowiedzialna za tworzenie wystąpień kontrolki. Każda Klasa kontrolki OLE musi mieć fabrykę klas.

Kolejną ważną cechą formantów OLE jest możliwość wymuszenia licencji. ControlWizard umożliwia włączenie licencjonowania podczas tworzenia projektu kontrolki. Aby uzyskać więcej informacji na temat kontroli licencjonowania, zobacz artykuł [formanty ActiveX: Licencjonowanie kontrolki ActiveX](../../mfc/mfc-activex-controls-licensing-an-activex-control.md).

W poniższej tabeli wymieniono kilka makr i funkcji służących do deklarowania i implementowania fabryki klasy kontrolki oraz do licencjonowania kontrolki.

### <a name="class-factories-and-licensing"></a>Fabryki klas i licencjonowanie

|Makro lub funkcja|Opis|
|-|-|
|[DECLARE_OLECREATE_EX](#declare_olecreate_ex)|Deklaruje fabrykę klasy dla kontrolki OLE lub strony właściwości.|
|[IMPLEMENT_OLECREATE_EX](#implement_olecreate_ex)|Implementuje funkcję kontrolki `GetClassID` i deklaruje wystąpienie fabryki klas.|
|[BEGIN_OLEFACTORY](#begin_olefactory)|Rozpoczyna deklarację wszelkich funkcji licencjonowania.|
|[END_OLEFACTORY](#end_olefactory)|Zakończenie deklaracji wszelkich funkcji licencjonowania.|
|[AfxVerifyLicFile](#afxverifylicfile)|Sprawdza, czy formant jest licencjonowany do użycia na określonym komputerze.|

## <a name="declare_olecreate_ex"></a><a name="declare_olecreate_ex"></a> DECLARE_OLECREATE_EX

Deklaruje fabrykę klasy i `GetClassID` funkcję członkowską klasy kontrolki.

```
DECLARE_OLECREATE_EX(class_name)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Nazwa klasy kontrolki.

### <a name="remarks"></a>Uwagi

Użyj tego makra w pliku nagłówkowym klasy kontrolki dla formantu, który nie obsługuje licencjonowania.

Należy zauważyć, że to makro służy do tego samego celu co przykładowy kod:

[!code-cpp[NVC_MFCAxCtl#14](../../mfc/reference/codesnippet/cpp/class-factories-and-licensing_1.h)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** 'afxctl. h

## <a name="implement_olecreate_ex"></a><a name="implement_olecreate_ex"></a> IMPLEMENT_OLECREATE_EX

Implementuje fabrykę klasy kontrolki i funkcję elementu członkowskiego [GetClassID](../../mfc/reference/colecontrol-class.md#getclassid) klasy formantu.

```
IMPLEMENT_OLECREATE_EX(
   class_name,
    external_name,
    l,
    w1,
    w2,
    b1,
    b2,
    b3,
    b4,
    b5,
    b6,
    b7,
    b8)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Nazwa klasy strony właściwości formantu.

*external_name*<br/>
Nazwa obiektu uwidoczniona dla aplikacji.

*l, W1, W2, B1, B2, B3, B4, B5, B6, B7, B8*<br/>
Składniki klasy CLSID. Aby uzyskać więcej informacji na temat tych parametrów, zobacz uwagi dotyczące [IMPLEMENT_OLECREATE](run-time-object-model-services.md#implement_olecreate).

### <a name="remarks"></a>Uwagi

To makro musi pojawić się w pliku implementacji dla każdej klasy kontrolki, która używa makra DECLARE_OLECREATE_EX lub makra BEGIN_OLEFACTORY i END_OLEFACTORY. Nazwa zewnętrzna to identyfikator kontrolki OLE, który jest udostępniany innym aplikacjom. Kontenery używają tej nazwy do żądania obiektu tej klasy kontrolki.

### <a name="requirements"></a>Wymagania

  **Nagłówek** 'afxctl. h

## <a name="begin_olefactory"></a><a name="begin_olefactory"></a> BEGIN_OLEFACTORY

Rozpoczyna deklarację fabryki klas w pliku nagłówkowym klasy formantu.

```
BEGIN_OLEFACTORY(class_name)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Określa nazwę klasy kontrolki, której fabrykę klas.

### <a name="remarks"></a>Uwagi

Deklaracje funkcji licencjonowania klasy fabryki powinny rozpoczynać się natychmiast po BEGIN_OLEFACTORY.

### <a name="requirements"></a>Wymagania

  **Nagłówek** 'afxctl. h

## <a name="end_olefactory"></a><a name="end_olefactory"></a> END_OLEFACTORY

Zakończenie deklaracji fabryki klas formantu.

```
END_OLEFACTORY(class_name)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Nazwa klasy kontrolki, której fabryki klas to.

### <a name="requirements"></a>Wymagania

  **Nagłówek** 'afxctl. h

## <a name="afxverifylicfile"></a><a name="afxverifylicfile"></a> AfxVerifyLicFile

Wywołaj tę funkcję, aby sprawdzić, czy plik licencji nazwany przez `pszLicFileName` jest prawidłowy dla kontrolki OLE.

```
BOOL AFXAPI AfxVerifyLicFile(
    HINSTANCE  hInstance,
    LPCTSTR  pszLicFileName,
    LPOLESTR  pszLicFileContents,
    UINT cch = -1);
```

### <a name="parameters"></a>Parametry

*hInstance*<br/>
Uchwyt wystąpienia biblioteki DLL skojarzonej z licencjonowaną kontrolką.

*pszLicFileName*<br/>
Wskazuje ciąg znaku zakończenia null zawierający nazwę pliku licencji.

*pszLicFileContents*<br/>
Wskazuje sekwencję bajtów, która musi być zgodna z sekwencją znalezioną na początku pliku licencji.

*cch*<br/>
Liczba znaków w *pszLicFileContents*.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli plik licencji istnieje i zaczyna się od sekwencji znaków w *pszLicFileContents*; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli *CCH* to-1, ta funkcja używa:

[!code-cpp[NVC_MFC_Utilities#36](../../mfc/codesnippet/cpp/class-factories-and-licensing_2.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** 'afxctl. h

## <a name="see-also"></a>Zobacz też

[Makra i Globals](../../mfc/reference/mfc-macros-and-globals.md)
