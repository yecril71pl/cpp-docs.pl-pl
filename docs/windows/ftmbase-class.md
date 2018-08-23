---
title: Ftmbase — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- ftm/Microsoft::WRL::FtmBase
dev_langs:
- C++
helpviewer_keywords:
- FtmBase class
ms.assetid: 275f3b71-2975-4f92-89e7-d351e96496df
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cb3b9ecae955ac78c6139156c3379fcd97511671
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42584376"
---
# <a name="ftmbase-class"></a>FtmBase — Klasa

Reprezentuje obiekt bezwątkowego.

## <a name="syntax"></a>Składnia

```cpp
class FtmBase : public Microsoft::WRL::Implements<
   Microsoft::WRL::RuntimeClassFlags<WinRtClassicComMix>,
   Microsoft::WRL::CloakedIid<IMarshal> >;
```

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [runtimeclass — klasa](runtimeclass-class.md).

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[FtmBase::FtmBase, konstruktor](../windows/ftmbase-ftmbase-constructor.md)|Inicjuje nowe wystąpienie klasy **FtmBase** klasy.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[FtmBase::CreateGlobalInterfaceTable, metoda](../windows/ftmbase-createglobalinterfacetable-method.md)|Tworzy tabelę interfejsu globalnego (GIT).|
|[FtmBase::DisconnectObject, metoda](../windows/ftmbase-disconnectobject-method.md)|Wymuś zwalnia wszystkie połączenia zewnętrzne do obiektu. Serwer obiektu wywołuje obiekt implementacja tej metody przed zamykanie.|
|[FtmBase::GetMarshalSizeMax, metoda](../windows/ftmbase-getmarshalsizemax-method.md)|Uzyskaj górnej granicy liczby bajtów potrzebnych do organizowania określony wskaźnik interfejsu do określonego obiektu.|
|[FtmBase::GetUnmarshalClass, metoda](../windows/ftmbase-getunmarshalclass-method.md)|Pobiera identyfikator klasy, który używa modelu COM, aby zlokalizować bibliotekę DLL zawierającego kod dla odpowiedniego serwera proxy. COM ładuje tę bibliotekę DLL, aby utworzyć wystąpienie niezainicjowanej serwera proxy.|
|[FtmBase::MarshalInterface, metoda](../windows/ftmbase-marshalinterface-method.md)|Zapisuje w strumieniu danych wymagane do zainicjowania obiektu serwera proxy, w niektórych procesu klienta.|
|[FtmBase::ReleaseMarshalData, metoda](../windows/ftmbase-releasemarshaldata-method.md)|Niszczy pakietów danych zorganizowanej.|
|[FtmBase::UnmarshalInterface, metoda](../windows/ftmbase-unmarshalinterface-method.md)|Inicjuje nowo utworzony serwer proxy i zwraca wskaźnik interfejsu do tego serwera proxy.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[FtmBase::marshaller_, składowa danych](../windows/ftmbase-marshaller-data-member.md)|Zawiera odwołanie do marshaler trybu.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`FtmBase`

## <a name="requirements"></a>Wymagania

**Nagłówek:** ftm.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL, przestrzeń nazw](../windows/microsoft-wrl-namespace.md)