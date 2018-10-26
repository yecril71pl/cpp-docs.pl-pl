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
ms.openlocfilehash: df0187364a44c84a2d0f7f38e968e0ea17df1fb2
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50064163"
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

- Inicjuje biblioteki COM w bieżącym apartamentu aplikacji wywołującej. Aby uzyskać więcej informacji, zobacz [OleInitialize](/windows/desktop/api/ole2/nf-ole2-oleinitialize).

- Tworzy obiekt filtr komunikatu Implementowanie [IMessageFilter](/windows/desktop/api/objidl/nn-objidl-imessagefilter) interfejsu. Ten filtr komunikatu jest możliwy z wywołaniem [afxolegetmessagefilter —](application-control.md#afxolegetmessagefilter).

> [!NOTE]
>  Jeśli **afxoleinit —** jest wywoływana z biblioteki MFC DLL wywołanie zakończy się niepowodzeniem. Błąd występuje, ponieważ funkcja zakłada, że jeśli zostanie wywołana z biblioteki DLL, OLE system był poprzednio inicjowany przez aplikacji wywołującej.

> [!NOTE]
>  Aplikacji MFC muszą być zainicjowane w formacie komórek wielowątkowych pojedynczego (STA). Jeśli wywołasz [CoInitializeEx](/windows/desktop/api/combaseapi/nf-combaseapi-coinitializeex) w swojej `InitInstance` zastąpienia, określ COINIT_APARTMENTTHREADED (zamiast COINIT_MULTITHREADED).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdisp.h

## <a name="see-also"></a>Zobacz też

[Makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md)
