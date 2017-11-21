---
title: Inicjalizacja OLE | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- afxdisp/AfxOleInit
- afxdisp/AfxEnableControlContainer
dev_langs: C++
helpviewer_keywords: OLE initialization
ms.assetid: aa8a54a7-24c3-4344-b2c6-dbcf6084fa31
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5fd0a194dc8f5b9272921a0445ecf5754ec2a4e7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ole-initialization"></a>Inicjalizacja OLE
Zanim aplikacji można użyć usług systemowych OLE, musi zainicjować OLE systemowej biblioteki dll i sprawdź, czy są zainstalowane poprawne wersje bibliotek DLL. **Afxoleinit —** funkcja inicjuje OLE systemowej biblioteki dll.  
  
### <a name="ole-initialization"></a>Inicjalizacja OLE  
  
|||  
|-|-|  
|[Afxoleinit —](#afxoleinit)|Inicjuje bibliotek OLE.| 
|[AfxEnableControlContainer](#afxenablecontrolcontainer)|Wywołanie tej funkcji w obiektu application `InitInstance` funkcji, aby włączyć obsługę zawierania formantów OLE.| 


## <a name="afxenablecontrolcontainer"></a>AfxEnableControlContainer
Wywołanie tej funkcji w obiektu application `InitInstance` funkcji, aby włączyć obsługę zawierania formantów OLE.  
   
### <a name="syntax"></a>Składnia    
```
void AfxEnableControlContainer( );  
```  
   
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji dotyczących formantów OLE (nazywane teraz formantów ActiveX), zobacz [tematy formantu ActiveX](../mfc-activex-controls.md).  
   
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdisp.h  

  
##  <a name="afxoleinit"></a>Afxoleinit —  
 Inicjowanie obsługi aplikacji.  
  
``` 
BOOL AFXAPI AfxOleInit(); 
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; 0, jeśli inicjowanie zakończy się niepowodzeniem, prawdopodobnie ponieważ niepoprawne wersje bibliotek DLL systemu OLE są zainstalowane.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji, aby zainicjować obsługę OLE aplikacji MFC. Gdy ta funkcja jest wywoływana, wykonywane są następujące akcje:  
  
-   Inicjuje biblioteki COM na bieżącego apartamentu aplikacji wywołującej. Aby uzyskać więcej informacji, zobacz [Funkcja OleInitialize](http://msdn.microsoft.com/library/windows/desktop/ms690134).  
  
-   Tworzy obiekt filtr komunikatu implementacja [IMessageFilter](http://msdn.microsoft.com/library/windows/desktop/ms693740) interfejsu. Ten filtr komunikatu jest możliwy przy użyciu wywołania do [afxolegetmessagefilter —](application-control.md#afxolegetmessagefilter).  
  
> [!NOTE]
>  Jeśli **afxoleinit —** jest wywoływana z biblioteki MFC DLL wywołanie zakończy się niepowodzeniem. Błąd występuje, ponieważ funkcja przyjęto założenie, że jeśli jest ona wywoływana z biblioteki DLL, systemu OLE był poprzednio inicjowany przez wywołanie aplikacji.  
  
> [!NOTE]
>  Aplikacje MFC musi zostać zainicjowany jako pojedynczy wątków typu apartment (STA). Jeśli należy wywołać [funkcja CoInitializeEx](http://msdn.microsoft.com/library/windows/desktop/ms695279) w Twojej `InitInstance` zastępowania, określ `COINIT_APARTMENTTHREADED` (zamiast `COINIT_MULTITHREADED`). Aby uzyskać więcej informacji, zobacz PRB: MFC aplikacja przestaje odpowiadać podczas inicjowania aplikacji jako wielowątkowe apartamentu (828643) w [http://support.microsoft.com/default.aspxscid=kb;en-us;828643](http://support.microsoft.com/default.aspxscid=kb;en-us;828643).  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdisp.h

## <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md)
