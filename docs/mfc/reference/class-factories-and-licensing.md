---
title: Fabryki klas i licencjonowanie
ms.date: 11/04/2016
helpviewer_keywords:
- class factories [MFC], and licensing
ms.assetid: 53c4856a-4062-46db-9f69-dd4339f746b3
ms.openlocfilehash: e3fed6520cdbe0fd964e4e80e7c9ed9b78296d16
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372307"
---
# <a name="class-factories-and-licensing"></a>Fabryki klas i licencjonowanie

Aby utworzyć wystąpienie formantu OLE, aplikacja kontenera wywołuje funkcję elementu członkowskiego fabryki klasy formantu. Ponieważ formant jest rzeczywisty obiekt OLE, fabryka klas jest odpowiedzialny za tworzenie wystąpień formantu. Każda klasa sterowania OLE musi mieć fabrykę klas.

Inną ważną cechą formantów OLE jest ich możliwość wymuszania licencji. ControlWizard pozwala na włączenie licencjonowania podczas tworzenia projektu sterowania. Aby uzyskać więcej informacji na temat licencjonowania kontroli, zobacz artykuł [ActiveX Controls: Licensing An ActiveX Control](../../mfc/mfc-activex-controls-licensing-an-activex-control.md).

W poniższej tabeli wymieniono kilka makr i funkcji używanych do deklarowania i implementowania fabryki klas formantu oraz licencjonowanie formantu.

### <a name="class-factories-and-licensing"></a>Fabryki klas i licencjonowanie

|||
|-|-|
|[DECLARE_OLECREATE_EX](#declare_olecreate_ex)|Deklaruje fabrykę klas dla formantu OLE lub strony właściwości.|
|[IMPLEMENT_OLECREATE_EX](#implement_olecreate_ex)|Implementuje `GetClassID` funkcję formantu i deklaruje wystąpienie fabryki klas.|
|[BEGIN_OLEFACTORY](#begin_olefactory)|Rozpoczyna się deklaracja wszelkich funkcji licencjonowania.|
|[END_OLEFACTORY](#end_olefactory)|Kończy deklarację wszelkich funkcji licencjonowania.|
|[AfxVerifyLicFile (AfxVerifyLicFile)](#afxverifylicfile)|Sprawdza, czy formant jest licencjonowany do użycia na określonym komputerze.|

## <a name="declare_olecreate_ex"></a><a name="declare_olecreate_ex"></a>DECLARE_OLECREATE_EX

Deklaruje fabrykę klas `GetClassID` i funkcję elementu członkowskiego klasy kontrolnej.

```
DECLARE_OLECREATE_EX(class_name)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Nazwa klasy formantu.

### <a name="remarks"></a>Uwagi

Użyj tego makra w pliku nagłówka klasy formantu dla formantu, który nie obsługuje licencjonowania.

Należy zauważyć, że to makro służy temu sameemu celowi, co poniższy przykładowy kod:

[!code-cpp[NVC_MFCAxCtl#14](../../mfc/reference/codesnippet/cpp/class-factories-and-licensing_1.h)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxctl.h

## <a name="implement_olecreate_ex"></a><a name="implement_olecreate_ex"></a>IMPLEMENT_OLECREATE_EX

Implementuje fabryki klas formantu i funkcji elementu członkowskiego [GetClassID](../../mfc/reference/colecontrol-class.md#getclassid) klasy kontroli.

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
Nazwa obiektu jest widoczna dla aplikacji.

*l, w1, w2, b1, b2, b3, b4, b5, b6, b7, b8*<br/>
Składniki clsid klasy. Aby uzyskać więcej informacji na temat tych parametrów, zobacz Uwagi dla [IMPLEMENT_OLECREATE](run-time-object-model-services.md#implement_olecreate).

### <a name="remarks"></a>Uwagi

To makro musi pojawić się w pliku implementacji dla każdej klasy formantu, która używa makra DECLARE_OLECREATE_EX lub makr BEGIN_OLEFACTORY i END_OLEFACTORY. Nazwa zewnętrzna jest identyfikatorem formantu OLE, który jest narażony na inne aplikacje. Kontenery używają tej nazwy, aby zażądać obiektu tej klasy formantu.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxctl.h

## <a name="begin_olefactory"></a><a name="begin_olefactory"></a>BEGIN_OLEFACTORY

Rozpoczyna deklarację fabryki klasy w pliku nagłówka klasy kontrolnej.

```
BEGIN_OLEFACTORY(class_name)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Określa nazwę klasy kontrolnej, której fabryka klasy jest fabryczna.

### <a name="remarks"></a>Uwagi

Deklaracje funkcji licencjonowania fabrycznego klasy powinny rozpocząć się natychmiast po BEGIN_OLEFACTORY.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxctl.h

## <a name="end_olefactory"></a><a name="end_olefactory"></a>END_OLEFACTORY

Kończy deklarację fabryki klasy kontroli.

```
END_OLEFACTORY(class_name)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Nazwa klasy kontrolnej, której fabryka klasy jest taka.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxctl.h

## <a name="afxverifylicfile"></a><a name="afxverifylicfile"></a>AfxVerifyLicFile (AfxVerifyLicFile)

Wywołanie tej funkcji, aby sprawdzić, czy plik licencji nazwany przez `pszLicFileName` jest prawidłowy dla formantu OLE.

```
BOOL AFXAPI AfxVerifyLicFile(
    HINSTANCE  hInstance,
    LPCTSTR  pszLicFileName,
    LPOLESTR  pszLicFileContents,
    UINT cch = -1);
```

### <a name="parameters"></a>Parametry

*hInstance (Nieumieja)*<br/>
Dojście wystąpienia biblioteki DLL skojarzone z kontrolką licencjonowaną.

*pszLicFileName*<br/>
Wskazuje ciąg znaków zakończonych wartością null zawierający nazwę pliku licencji.

*pszLicFileContents*<br/>
Wskazuje sekwencję bajtów, która musi być zgodna z sekwencją znajdującą się na początku pliku licencji.

*Cch*<br/>
Liczba znaków w *pszLicFileContents*.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli plik licencji istnieje i zaczyna się od sekwencji znaków w *pszLicFileContents*; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli *cch* wynosi -1, ta funkcja używa:

[!code-cpp[NVC_MFC_Utilities#36](../../mfc/codesnippet/cpp/class-factories-and-licensing_2.cpp)]

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxctl.h

## <a name="see-also"></a>Zobacz też

[Makra i globals](../../mfc/reference/mfc-macros-and-globals.md)
