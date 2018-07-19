---
title: Inicjalizacja OLE | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- afxdisp/AfxOleInit
- afxdisp/AfxEnableControlContainer
dev_langs:
- C++
helpviewer_keywords:
- OLE initialization
ms.assetid: aa8a54a7-24c3-4344-b2c6-dbcf6084fa31
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 330701c4fcc75d40e782d25baa55044b88852f50
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2018
ms.locfileid: "37337800"
---
# <a name="ole-initialization"></a>Inicjalizacja OLE
Zanim aplikacja może użyć usługi systemowe OLE, musi zainicjować OLE systemowych bibliotek DLL i sprawdź, czy biblioteki DLL są w poprawnej wersji. `AfxOleInit` Funkcja inicjuje OLE systemowych bibliotek DLL.  
  
### <a name="ole-initialization"></a>Inicjalizacja OLE  
  
|||  
|-|-|  
|[Afxoleinit —](#afxoleinit)|Inicjuje bibliotek OLE.| 
|[Afxenablecontrolcontainer —](#afxenablecontrolcontainer)|Wywołaj tę funkcję w obiekt aplikacji `InitInstance` funkcję, aby włączyć obsługę zawierania formantów OLE.| 


## <a name="afxenablecontrolcontainer"></a> Afxenablecontrolcontainer —
Wywołaj tę funkcję w obiekt aplikacji `InitInstance` funkcję, aby włączyć obsługę zawierania formantów OLE.  
   
### <a name="syntax"></a>Składnia    
```
void AfxEnableControlContainer( );  
```  
   
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat formantów OLE (obecnie nazywanego formantów ActiveX), zobacz [tematy formantu ActiveX](../mfc-activex-controls.md).  
   
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdisp.h  

  
##  <a name="afxoleinit"></a>  Afxoleinit —  
 Inicjowanie obsługi aplikacji.  
  
``` 
BOOL AFXAPI AfxOleInit(); 
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; 0, jeśli inicjowanie zakończy się niepowodzeniem, prawdopodobnie ponieważ niepoprawnej wersji bibliotek DLL systemu OLE są zainstalowane.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj tę funkcję można zainicjować obsługi OLE dla aplikacji MFC. Gdy ta funkcja jest wywoływana, są wykonywane następujące akcje:  
  
-   Inicjuje biblioteki COM w bieżącym apartamentu aplikacji wywołującej. Aby uzyskać więcej informacji, zobacz [OleInitialize](http://msdn.microsoft.com/library/windows/desktop/ms690134).  
  
-   Tworzy obiekt filtr komunikatu Implementowanie [IMessageFilter](http://msdn.microsoft.com/library/windows/desktop/ms693740) interfejsu. Ten filtr komunikatu jest możliwy z wywołaniem [afxolegetmessagefilter —](application-control.md#afxolegetmessagefilter).  
  
> [!NOTE]
>  Jeśli **afxoleinit —** jest wywoływana z biblioteki MFC DLL wywołanie zakończy się niepowodzeniem. Błąd występuje, ponieważ funkcja zakłada, że jeśli zostanie wywołana z biblioteki DLL, OLE system był poprzednio inicjowany przez aplikacji wywołującej.  
  
> [!NOTE]
>  Aplikacji MFC muszą być zainicjowane w formacie komórek wielowątkowych pojedynczego (STA). Jeśli wywołasz [CoInitializeEx](http://msdn.microsoft.com/library/windows/desktop/ms695279) w swojej `InitInstance` zastąpienia, określ COINIT_APARTMENTTHREADED (zamiast COINIT_MULTITHREADED). Aby uzyskać więcej informacji, zobacz PRB: Aplikacja MFC przestaje odpowiadać podczas inicjowania aplikacji jako wielowątkowe apartamentu (828643) na [ http://support.microsoft.com/default.aspxscid=kb; en-us; 828643](http://support.microsoft.com/default.aspxscid=kb;en-us;828643).  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdisp.h

## <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md)
