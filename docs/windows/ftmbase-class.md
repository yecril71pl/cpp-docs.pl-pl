---
title: Ftmbase — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- ftm/Microsoft::WRL::FtmBase
dev_langs:
- C++
helpviewer_keywords:
- FtmBase class
ms.assetid: 275f3b71-2975-4f92-89e7-d351e96496df
caps.latest.revision: ''
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9499a5a30f99e639137532aad1763b434a196809
ms.sourcegitcommit: 1d11412c8f5e6ddf4edded89e0ef5097cc89f812
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2018
---
# <a name="ftmbase-class"></a>FtmBase — Klasa
Reprezentuje obiekt opcja.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
class FtmBase : public Microsoft::WRL::Implements<  
   Microsoft::WRL::RuntimeClassFlags<WinRtClassicComMix>,   
   Microsoft::WRL::CloakedIid<IMarshal> >;  
```  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji zobacz temat "IMarshal" w podrzędny "Interfejsy COM" w temacie "Odwołania COM" w bibliotece MSDN.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[FtmBase::FtmBase, konstruktor](../windows/ftmbase-ftmbase-constructor.md)|Inicjuje nowe wystąpienie klasy ftmbase —.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[FtmBase::CreateGlobalInterfaceTable, metoda](../windows/ftmbase-createglobalinterfacetable-method.md)|Tworzy tabelę interfejsu globalnego (GIT).|  
|[FtmBase::DisconnectObject, metoda](../windows/ftmbase-disconnectobject-method.md)|Wymuszanie zwalnia wszystkie połączenia zewnętrzne do obiektu. Serwer obiektu wywołuje obiektu implementacja tej metody przed zamykanie.|  
|[FtmBase::GetMarshalSizeMax, metoda](../windows/ftmbase-getmarshalsizemax-method.md)|Pobierz górnej granicy liczby bajtów potrzebne do organizowania wskaźników określonego interfejsu w określonym obiekcie.|  
|[FtmBase::GetUnmarshalClass, metoda](../windows/ftmbase-getunmarshalclass-method.md)|Pobiera identyfikator klasy, który COM używa do lokalizowania biblioteki DLL zawierającej kod dla odpowiedniego serwera proxy. COM ładuje tę bibliotekę DLL, można utworzyć niezainicjowanych wystąpienia serwera proxy.|  
|[FtmBase::MarshalInterface, metoda](../windows/ftmbase-marshalinterface-method.md)|Zapisuje do strumienia dane wymagane do zainicjowania obiektu serwera proxy, w niektórych procesu klienta.|  
|[FtmBase::ReleaseMarshalData, metoda](../windows/ftmbase-releasemarshaldata-method.md)|Niszczy pakiet danych organizowane.|  
|[FtmBase::UnmarshalInterface, metoda](../windows/ftmbase-unmarshalinterface-method.md)|Inicjuje nowo utworzonego serwera proxy i zwraca wskaźnika interfejsu do tego serwera proxy.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[FtmBase::marshaller_, składowa danych](../windows/ftmbase-marshaller-data-member.md)|Zawiera odwołanie do Organizator trybu wolnych wątków.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `FtmBase`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** ftm.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL, przestrzeń nazw](../windows/microsoft-wrl-namespace.md)