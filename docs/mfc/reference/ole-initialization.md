---
title: Inicjalizacja OLE
ms.date: 11/04/2016
f1_keywords:
- afxdisp/AfxOleInit
- afxdisp/AfxEnableControlContainer
helpviewer_keywords:
- OLE initialization
ms.assetid: aa8a54a7-24c3-4344-b2c6-dbcf6084fa31
ms.openlocfilehash: 13c267df492ab86606e893df4c13e5510e6e546a
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88843693"
---
# <a name="ole-initialization"></a>Inicjalizacja OLE

Aby aplikacja mogła korzystać z usług systemu OLE, musi zainicjować biblioteki DLL systemu OLE i sprawdzić, czy biblioteki DLL są poprawne. `AfxOleInit`Funkcja inicjuje biblioteki DLL systemu OLE.

### <a name="ole-initialization"></a>Inicjalizacja OLE

|Nazwa|Opis|
|-|-|
|[AfxOleInit](#afxoleinit)|Inicjuje biblioteki OLE.|
|[AfxEnableControlContainer —](#afxenablecontrolcontainer)|Wywołaj tę funkcję w funkcji obiektu aplikacji `InitInstance` , aby włączyć obsługę funkcji zawierania formantów OLE.|

## <a name="afxenablecontrolcontainer"></a><a name="afxenablecontrolcontainer"></a> AfxEnableControlContainer —

Wywołaj tę funkcję w funkcji obiektu aplikacji `InitInstance` , aby włączyć obsługę funkcji zawierania formantów OLE.

### <a name="syntax"></a>Składnia

```cpp
void AfxEnableControlContainer( );
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat kontrolek OLE (nazywanych teraz kontrolkami ActiveX), zobacz [temat kontrolki ActiveX](../mfc-activex-controls.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFXDISP. h

## <a name="afxoleinit"></a><a name="afxoleinit"></a> AfxOleInit

Inicjuje obsługę OLE dla aplikacji.

```
BOOL AFXAPI AfxOleInit();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; 0 Jeśli inicjalizacja nie powiedzie się, prawdopodobnie ponieważ zainstalowano niepoprawne wersje bibliotek DLL systemu OLE.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, aby zainicjować obsługę OLE dla aplikacji MFC. Gdy ta funkcja jest wywoływana, wykonywane są następujące akcje:

- Inicjuje bibliotekę COM w bieżącej apartamentu aplikacji wywołującej. Aby uzyskać więcej informacji, zobacz [OleInitialize](/windows/win32/api/ole2/nf-ole2-oleinitialize).

- Tworzy obiekt filtru komunikatów, implementując Interfejs [IMessageFilter](/windows/win32/api/objidl/nn-objidl-imessagefilter) . Dostęp do tego filtru komunikatów można uzyskać za pomocą wywołania [AfxOleGetMessageFilter](application-control.md#afxolegetmessagefilter).

> [!NOTE]
> Jeśli **AfxOleInit** jest wywoływana z biblioteki MFC DLL, wywołanie zakończy się niepowodzeniem. Błąd występuje, ponieważ funkcja zakłada, że jeśli jest wywoływana z biblioteki DLL, system OLE został wcześniej zainicjowany przez aplikację wywołującą.

> [!NOTE]
> Aplikacje MFC muszą być zainicjowane jako Apartament jednowątkowy (STA). Jeśli wywołasz [CoInitializeEx](/windows/win32/api/combaseapi/nf-combaseapi-coinitializeex) w `InitInstance` przesłonięciu, określ COINIT_APARTMENTTHREADED (a nie COINIT_MULTITHREADED).

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFXDISP. h

## <a name="see-also"></a>Zobacz też

[Makra i Globals](../../mfc/reference/mfc-macros-and-globals.md)
