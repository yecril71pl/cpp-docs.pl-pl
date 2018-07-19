---
title: Afx_extension_module — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- AFX_EXTENSION_MODULE
dev_langs:
- C++
helpviewer_keywords:
- AFX_EXTENSION_MODULE structure [MFC]
ms.assetid: b85a989c-d0c5-4b28-b53c-dad45b75704e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 65f1f2a6416ef93395f7ec73b27a89bf44e2d885
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2018
ms.locfileid: "37339387"
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
 *bInitialized*  
 Wartość TRUE, jeśli moduł DLL została zainicjowana przy użyciu `AfxInitExtensionModule`.  
  
 *hModule*  
 Określa uchwytu modułu DLL.  
  
 *hResource*  
 Określa uchwytu modułu DLL zasobów niestandardowych.  
  
 *pFirstSharedClass*  
 Wskaźnik do informacji ( `CRuntimeClass` struktury) o pierwszej klasie czasu wykonywania modułu DLL. Służą do początku listy klas środowiska uruchomieniowego.  
  
 *pFirstSharedFactory*  
 Wskaźnik do pierwszego fabryki obiektów modułu DLL ( `COleObjectFactory` obiektu). Służą do początku lista fabryk klas.  
  
## <a name="remarks"></a>Uwagi  
 Rozszerzenia MFC biblioteki DLL trzeba wykonać dwie czynności w ich `DllMain` funkcji:  
  
-   Wywołaj [afxinitextensionmodule —](extension-dll-macros.md#afxinitextensionmodule) i sprawdź wartość zwracaną.  
  
-   Tworzenie `CDynLinkLibrary` obiektu, jeśli biblioteka DLL będzie eksportowanie [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiektów lub ma swoje własne niestandardowe zasoby.  
  
 `AFX_EXTENSION_MODULE` Struktury jest używany do przechowywania kopii rozszerzeń MFC DLL modułu stanu, w tym kopiowania obiektów klasy środowiska uruchomieniowego, które zostały zainicjowane przez rozszerzenia MFC biblioteki DLL jako część konstruowania normalnych obiektu statycznego wykonywane przed `DllMain` jest wprowadzony. Na przykład:  
  
 [!code-cpp[NVC_MFC_DLL#2](../../atl-mfc-shared/codesnippet/cpp/afx-extension-module-structure_1.cpp)]  
  
 Moduł informacji przechowywanych w `AFX_EXTENSION_MODULE` struktury mogą być kopiowane do `CDynLinkLibrary` obiektu. Na przykład:  
  
 [!code-cpp[NVC_MFC_DLL#5](../../atl-mfc-shared/codesnippet/cpp/afx-extension-module-structure_2.cpp)]  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afx.h  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [Afxinitextensionmodule —](extension-dll-macros.md#afxinitextensionmodule)   
 [Afxtermextensionmodule —](extension-dll-macros.md#afxtermextensionmodule)

