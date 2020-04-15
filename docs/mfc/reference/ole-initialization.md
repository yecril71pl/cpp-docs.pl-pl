---
title: Inicjalizacja OLE
ms.date: 11/04/2016
f1_keywords:
- afxdisp/AfxOleInit
- afxdisp/AfxEnableControlContainer
helpviewer_keywords:
- OLE initialization
ms.assetid: aa8a54a7-24c3-4344-b2c6-dbcf6084fa31
ms.openlocfilehash: 39a6f28bfe38f254f15f441ed6305daa2cb5793e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373031"
---
# <a name="ole-initialization"></a>Inicjalizacja OLE

Zanim aplikacja będzie mogła korzystać z usług systemu OLE, musi zainicjować biblioteki DLL systemu OLE i sprawdzić, czy biblioteki DLL są poprawną wersją. Funkcja `AfxOleInit` inicjuje biblioteki DLL systemu OLE.

### <a name="ole-initialization"></a>Inicjalizacja OLE

|||
|-|-|
|[Afxoleinit](#afxoleinit)|Inicjuje biblioteki OLE.|
|[AfxEnableControlKontainer](#afxenablecontrolcontainer)|Wywołanie tej funkcji w `InitInstance` funkcji obiektu aplikacji, aby włączyć obsługę zamknięcia formantów OLE.|

## <a name="afxenablecontrolcontainer"></a><a name="afxenablecontrolcontainer"></a>AfxEnableControlKontainer

Wywołanie tej funkcji w `InitInstance` funkcji obiektu aplikacji, aby włączyć obsługę zamknięcia formantów OLE.

### <a name="syntax"></a>Składnia

```
void AfxEnableControlContainer( );
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat formantów OLE (nazywanych teraz formantami ActiveX), zobacz [Tematy sterowania ActiveX](../mfc-activex-controls.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdisp.h

## <a name="afxoleinit"></a><a name="afxoleinit"></a>Afxoleinit

Inicjuje obsługę OLE dla aplikacji.

```
BOOL AFXAPI AfxOleInit();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; 0 jeśli inicjowanie nie powiedzie się, prawdopodobnie dlatego, że są zainstalowane niepoprawne wersje bibliotek DLL systemu OLE.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji, aby zainicjować obsługę OLE dla aplikacji MFC. Gdy ta funkcja jest wywoływana, występują następujące akcje:

- Inicjuje bibliotekę COM w bieżącym mieszkaniu aplikacji wywołującej. Aby uzyskać więcej informacji, zobacz [OleInitialize](/windows/win32/api/ole2/nf-ole2-oleinitialize).

- Tworzy obiekt filtru wiadomości, implementując interfejs [IMessageFilter.](/windows/win32/api/objidl/nn-objidl-imessagefilter) Ten filtr wiadomości można uzyskać za pomocą połączenia [z AfxOleGetMessageFilter](application-control.md#afxolegetmessagefilter).

> [!NOTE]
> Jeśli **AfxOleInit** jest wywoływana z biblioteki DLL MFC, wywołanie zakończy się niepowodzeniem. Błąd występuje, ponieważ funkcja zakłada, że jeśli jest wywoływana z biblioteki DLL, system OLE został wcześniej zainicjowany przez aplikację wywołującą.

> [!NOTE]
> Aplikacje MFC muszą być inicjowane jako jednowątkowy apartament (STA). Jeśli wywołasz [CoInitializeEx](/windows/win32/api/combaseapi/nf-combaseapi-coinitializeex) w przesłonie, `InitInstance` określ COINIT_APARTMENTTHREADED (a nie COINIT_MULTITHREADED).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdisp.h

## <a name="see-also"></a>Zobacz też

[Makra i globals](../../mfc/reference/mfc-macros-and-globals.md)
