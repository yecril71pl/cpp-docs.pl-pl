---
title: "Afx_extension_module — struktura | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AFX_EXTENSION_MODULE
dev_langs:
- C++
helpviewer_keywords:
- AFX_EXTENSION_MODULE structure [MFC]
ms.assetid: b85a989c-d0c5-4b28-b53c-dad45b75704e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b4ac896fb16aa3c338cadd6273e226eebe986ae7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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
  
 `hModule`  
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
  
-   Utwórz **CDynLinkLibrary** obiektu, jeśli zostanie wyeksportowany plik DLL [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiektów lub ma własne niestandardowe zasoby.  
  
 `AFX_EXTENSION_MODULE` Struktura jest używana do przechowywania kopii rozszerzenia MFC DLL modułu Państwa, w tym kopiowania obiektów klasy środowiska uruchomieniowego, które zostały zainicjowane przez bibliotekę DLL rozszerzenia MFC jako część konstrukcji obiektu statycznego normalne wykonywany przed `DllMain` jest wprowadzona. Na przykład:  
  
 [!code-cpp[NVC_MFC_DLL#2](../../atl-mfc-shared/codesnippet/cpp/afx-extension-module-structure_1.cpp)]  
  
 Moduł informacji przechowywanych w `AFX_EXTENSION_MODULE` struktury mogą być kopiowane do **CDynLinkLibrary** obiektu. Na przykład:  
  
 [!code-cpp[NVC_MFC_DLL#5](../../atl-mfc-shared/codesnippet/cpp/afx-extension-module-structure_2.cpp)]  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afx.h  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [Afxinitextensionmodule —](extension-dll-macros.md#afxinitextensionmodule)   
 [Afxtermextensionmodule —](extension-dll-macros.md#afxtermextensionmodule)

