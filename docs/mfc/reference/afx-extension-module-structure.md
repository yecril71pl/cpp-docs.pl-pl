---
title: AFX_EXTENSION_MODULE — Struktura
ms.date: 11/04/2016
f1_keywords:
- AFX_EXTENSION_MODULE
helpviewer_keywords:
- AFX_EXTENSION_MODULE structure [MFC]
ms.assetid: b85a989c-d0c5-4b28-b53c-dad45b75704e
ms.openlocfilehash: ee39fcec3083145dbc23c7739897bf89d47578a6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50539038"
---
# <a name="afxextensionmodule-structure"></a>AFX_EXTENSION_MODULE — Struktura

`AFX_EXTENSION_MODULE` Jest używany podczas inicjowania biblioteki DLL rozszerzeń MFC do przechowywania stanu modułu MFC DLL rozszerzenia.

## <a name="syntax"></a>Składnia

```
struct AFX_EXTENSION_MODULE
{
    BOOL bInitialized;
    HMODULE hModule;
    HMODULE hResource;
    CRuntimeClass* pFirstSharedClass;
    COleObjectFactory* pFirstSharedFactory;
};
```

#### <a name="parameters"></a>Parametry

*bInitialized*<br/>
Wartość TRUE, jeśli moduł DLL została zainicjowana przy użyciu `AfxInitExtensionModule`.

*hModule*<br/>
Określa uchwytu modułu DLL.

*hResource*<br/>
Określa uchwytu modułu DLL zasobów niestandardowych.

*pFirstSharedClass*<br/>
Wskaźnik do informacji ( `CRuntimeClass` struktury) o pierwszej klasie czasu wykonywania modułu DLL. Służą do początku listy klas środowiska uruchomieniowego.

*pFirstSharedFactory*<br/>
Wskaźnik do pierwszego fabryki obiektów modułu DLL ( `COleObjectFactory` obiektu). Służą do początku lista fabryk klas.

## <a name="remarks"></a>Uwagi

Rozszerzenia MFC biblioteki DLL trzeba wykonać dwie czynności w ich `DllMain` funkcji:

- Wywołaj [afxinitextensionmodule —](extension-dll-macros.md#afxinitextensionmodule) i sprawdź wartość zwracaną.

- Tworzenie `CDynLinkLibrary` obiektu, jeśli biblioteka DLL będzie eksportowanie [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiektów lub ma swoje własne niestandardowe zasoby.

`AFX_EXTENSION_MODULE` Struktury jest używany do przechowywania kopii rozszerzeń MFC DLL modułu stanu, w tym kopiowania obiektów klasy środowiska uruchomieniowego, które zostały zainicjowane przez rozszerzenia MFC biblioteki DLL jako część konstruowania normalnych obiektu statycznego wykonywane przed `DllMain` jest wprowadzony. Na przykład:

[!code-cpp[NVC_MFC_DLL#2](../../atl-mfc-shared/codesnippet/cpp/afx-extension-module-structure_1.cpp)]

Moduł informacji przechowywanych w `AFX_EXTENSION_MODULE` struktury mogą być kopiowane do `CDynLinkLibrary` obiektu. Na przykład:

[!code-cpp[NVC_MFC_DLL#5](../../atl-mfc-shared/codesnippet/cpp/afx-extension-module-structure_2.cpp)]

## <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

## <a name="see-also"></a>Zobacz też

[Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[Afxinitextensionmodule —](extension-dll-macros.md#afxinitextensionmodule)<br/>
[Afxtermextensionmodule —](extension-dll-macros.md#afxtermextensionmodule)

