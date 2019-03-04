---
title: Inicjalizacja OLE
ms.date: 11/04/2016
f1_keywords:
- afxdisp/AfxOleInit
- afxdisp/AfxEnableControlContainer
helpviewer_keywords:
- OLE initialization
ms.assetid: aa8a54a7-24c3-4344-b2c6-dbcf6084fa31
ms.openlocfilehash: 3d49b37ffc2561fa9a51463a893ec2ba4f4fb725
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57304031"
---
# <a name="ole-initialization"></a>Inicjalizacja OLE

Zanim aplikacja może użyć usługi systemowe OLE, musi zainicjować OLE systemowych bibliotek DLL i sprawdź, czy biblioteki DLL są w poprawnej wersji. `AfxOleInit` Funkcja inicjuje OLE systemowych bibliotek DLL.

### <a name="ole-initialization"></a>Inicjalizacja OLE

|||
|-|-|
|[AfxOleInit](#afxoleinit)|Inicjuje bibliotek OLE.|
|[AfxEnableControlContainer](#afxenablecontrolcontainer)|Wywołaj tę funkcję w obiekt aplikacji `InitInstance` funkcję, aby włączyć obsługę zawierania formantów OLE.|

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

- Inicjuje biblioteki COM w bieżącym apartamentu aplikacji wywołującej. Aby uzyskać więcej informacji, zobacz [OleInitialize](/windows/desktop/api/ole2/nf-ole2-oleinitialize).

- Tworzy obiekt filtr komunikatu Implementowanie [IMessageFilter](/windows/desktop/api/objidl/nn-objidl-imessagefilter) interfejsu. Ten filtr komunikatu jest możliwy z wywołaniem [afxolegetmessagefilter —](application-control.md#afxolegetmessagefilter).

> [!NOTE]
>  Jeśli **afxoleinit —** jest wywoływana z biblioteki MFC DLL wywołanie zakończy się niepowodzeniem. Błąd występuje, ponieważ funkcja zakłada, że jeśli zostanie wywołana z biblioteki DLL, OLE system był poprzednio inicjowany przez aplikacji wywołującej.

> [!NOTE]
>  Aplikacji MFC muszą być zainicjowane w formacie komórek wielowątkowych pojedynczego (STA). Jeśli wywołasz [CoInitializeEx](/windows/desktop/api/combaseapi/nf-combaseapi-coinitializeex) w swojej `InitInstance` zastąpienia, określ COINIT_APARTMENTTHREADED (zamiast COINIT_MULTITHREADED).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdisp.h

## <a name="see-also"></a>Zobacz także

[Makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md)
