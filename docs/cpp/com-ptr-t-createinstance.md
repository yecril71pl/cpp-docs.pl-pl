---
title: _com_ptr_t::CreateInstance | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_ptr_t::CreateInstance
dev_langs:
- C++
helpviewer_keywords:
- CreateInstance method [C++]
ms.assetid: ab89b0e1-9da3-4784-a079-58b17340f111
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c8aca9422c4798cd798d048ce42443c4f38bd170
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37947851"
---
# <a name="comptrtcreateinstance"></a>_com_ptr_t::CreateInstance
**Microsoft Specific**  
  
 Tworzy nowe wystąpienie obiektu, biorąc pod uwagę `CLSID` lub `ProgID`.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
HRESULT CreateInstance(  
   const CLSID& rclsid,  
   IUnknown* pOuter=NULL,  
   DWORD dwClsContext = CLSCTX_ALL   
) throw( );  
HRESULT CreateInstance(  
   LPCWSTR clsidString,  
   IUnknown* pOuter=NULL,  
   DWORD dwClsContext = CLSCTX_ALL   
) throw( );  
HRESULT CreateInstance(  
   LPCSTR clsidStringA,  
   IUnknown* pOuter=NULL,  
   DWORD dwClsContext = CLSCTX_ALL   
) throw( );  
```  
  
#### <a name="parameters"></a>Parametry  
 *rclsid*  
 `CLSID` Obiektu.  
  
 *clsidString*  
 Ciąg Unicode, który zawiera jedną `CLSID` (począwszy od "**{**") lub `ProgID`.  
  
 *clsidStringA*  
 Wielobajtowy ciąg przy użyciu stronę kodową ANSI, który zawiera jedną `CLSID` (począwszy od "**{**") lub `ProgID`.  
  
 *dwClsContext*  
 Kontekst do uruchamiania kodu wykonywalnego.  
  
 *pOuter*  
 Zewnętrzne nieznany dla [agregacji](../atl/aggregation.md).  
  
## <a name="remarks"></a>Uwagi  
 Te funkcje elementów członkowskich wywołać `CoCreateInstance` Aby utworzyć nowy obiekt COM, a następnie zapytania dla typu interfejsu to inteligentny wskaźnik. Wskaźnik wynikowy następnie są hermetyzowane w ramach tej `_com_ptr_t` obiektu. `Release` jest wywoływana, aby zmniejszyć licznikiem odwołań do wcześniej zhermetyzowanego wskaźnika. Ta procedura zwraca wartość HRESULT do wskazania powodzenia lub niepowodzenia.  
  
-   **CreateInstance — (***rclsid* **,***dwClsContext***)** tworzy nowe wystąpienie uruchomionego obiektu, biorąc pod uwagę `CLSID`.        
  
-   **CreateInstance — (***clsidString* **,***dwClsContext***)** tworzy nowe wystąpienie uruchomionej danego obiektu Ciąg w formacie Unicode, który zawiera jedną `CLSID` (począwszy od "**{**") lub `ProgID`.        
  
-   **CreateInstance — (***clsidStringA* **,***dwClsContext***)** tworzy nowe wystąpienie uruchomionej danego obiektu ciąg znaków wielobajtowych, który zawiera jedną `CLSID` (począwszy od "**{**") lub `ProgID`.       Wywołania [MultiByteToWideChar](http://msdn.microsoft.com/library/windows/desktop/dd319072), która zakłada, że ten ciąg jest w stronę kodową ANSI zamiast stronę kodową OEM.  
  
 **END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [_com_ptr_t, klasa](../cpp/com-ptr-t-class.md)