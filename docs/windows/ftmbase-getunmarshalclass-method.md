---
title: FtmBase::GetUnmarshalClass, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- ftm/Microsoft::WRL::FtmBase::GetUnmarshalClass
dev_langs:
- C++
helpviewer_keywords:
- GetUnmarshalClass method
ms.assetid: 535fc539-5b97-4967-b158-f7568f13d341
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c76c2d75f3d8c2e872b29d9ecf07841c99027713
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42599506"
---
# <a name="ftmbasegetunmarshalclass-method"></a>FtmBase::GetUnmarshalClass — Metoda

Pobiera identyfikator klasy, który używa modelu COM, aby zlokalizować bibliotekę DLL zawierającego kod dla odpowiedniego serwera proxy. COM ładuje tę bibliotekę DLL, aby utworzyć wystąpienie niezainicjowanej serwera proxy.

## <a name="syntax"></a>Składnia

```cpp
STDMETHODIMP GetUnmarshalClass(
   __in REFIID riid,
   __in_opt void *pv,
   __in DWORD dwDestContext,
   __reserved void *pvDestContext,
   __in DWORD mshlflags,
   __out CLSID *pCid
) override;
```

### <a name="parameters"></a>Parametry

*Parametr riid*  
Odwołanie do identyfikatora interfejsu aby być organizowany.

*Wa*  
Wskaźnik do interfejsu, aby zorganizować; może mieć wartości NULL, jeśli obiekt wywołujący nie ma wskaźnik do żądanego interfejsu.

*dwDestContext*  
Miejsce docelowe kontekst, w którym ma zostać wycofana określonego interfejsu.

Określ co najmniej jednej wartości wyliczenia MSHCTX.

Unmarshaling może wystąpić w innym apartamentu bieżącego procesu (MSHCTX_INPROC) lub w inny proces na tym samym komputerze, co bieżący proces (MSHCTX_LOCAL).

*pvDestContext*  
Zarezerwowane dla przyszłego użytku; musi mieć wartość NULL.

*mshlflags*  
Gdy ta operacja zostanie ukończone, wskaźnik do CLSID, który ma być używany do tworzenia serwera proxy w procesie klienta.

*pCid*

## <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie wartość S_FALSE.

## <a name="requirements"></a>Wymagania

**Nagłówek:** ftm.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Zobacz też

[FtmBase, klasa](../windows/ftmbase-class.md)