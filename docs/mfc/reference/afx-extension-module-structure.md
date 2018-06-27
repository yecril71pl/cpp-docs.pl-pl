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
ms.openlocfilehash: e741f172d0dfe528a166fad087460fd9ae18c0f3
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36951185"
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
 **Wartość TRUE,** Jeśli modułu DLL został zainicjowany z `AfxInitExtensionModule`.  
  
 *hModule*  
 Określa dojście modułu DLL.  
  
 *hResource*  
 Określa dojście modułu DLL zasobów niestandardowych.  
  
 *pFirstSharedClass*  
 Wskaźnik do informacji ( `CRuntimeClass` struktury) informacje o klasie czasu wykonywania z pierwszego modułu DLL. Służą do początku listy klas środowiska wykonawczego.  
  
 *pFirstSharedFactory*  
 Wskaźnik do pierwszego fabrykę obiektów modułu DLL ( `COleObjectFactory` obiektu). Służą do początku listy fabryki klasy.  
  
## <a name="remarks"></a>Uwagi  
 Rozszerzenia MFC DLL należy wykonać dwie czynności w ich `DllMain` funkcji:  
  
-   Wywołanie [afxinitextensionmodule —](extension-dll-macros.md#afxinitextensionmodule) i sprawdzić wartość zwrotną.  
  
-   Utwórz `CDynLinkLibrary` obiektu, jeśli zostanie wyeksportowany plik DLL [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiektów lub ma własne niestandardowe zasoby.  
  
 `AFX_EXTENSION_MODULE` Struktura jest używana do przechowywania kopii rozszerzenia MFC DLL modułu Państwa, w tym kopiowania obiektów klasy środowiska uruchomieniowego, które zostały zainicjowane przez bibliotekę DLL rozszerzenia MFC jako część konstrukcji obiektu statycznego normalne wykonywany przed `DllMain` jest wprowadzona. Na przykład:  
  
 [!code-cpp[NVC_MFC_DLL#2](../../atl-mfc-shared/codesnippet/cpp/afx-extension-module-structure_1.cpp)]  
  
 Moduł informacji przechowywanych w `AFX_EXTENSION_MODULE` struktury mogą być kopiowane do `CDynLinkLibrary` obiektu. Na przykład:  
  
 [!code-cpp[NVC_MFC_DLL#5](../../atl-mfc-shared/codesnippet/cpp/afx-extension-module-structure_2.cpp)]  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afx.h  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [Afxinitextensionmodule —](extension-dll-macros.md#afxinitextensionmodule)   
 [Afxtermextensionmodule —](extension-dll-macros.md#afxtermextensionmodule)

