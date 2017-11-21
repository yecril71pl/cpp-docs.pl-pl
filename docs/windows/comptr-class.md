---
title: "Comptr — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: client/Microsoft::WRL::ComPtr
dev_langs: C++
helpviewer_keywords: ComPtr class
ms.assetid: a6551902-6819-478a-8df7-b6f312ab1fb0
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 96b46fe15b2c101ed3ebc8bb58033074f409b41c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="comptr-class"></a>ComPtr — Klasa
Tworzy *wskaźnika inteligentnego* typu, który reprezentuje interfejs określonej przez parametr szablonu. Comptr — automatycznie przechowuje licznika odwołań do podstawowej wskaźnika interfejsu i zwalnia interfejsu, gdy liczba odwołań do zera.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <  
   typename T  
>  
class ComPtr;  
  
template<  
   class U  
>  
friend class ComPtr;  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Interfejs, który reprezentuje comptr —.  
  
 `U`  
 Klasa bieżącej comptr — jest znajomym. (Szablon, który używa tego parametru jest chroniony).  
  
## <a name="remarks"></a>Uwagi  
 Comptr — <> deklaruje typ, który reprezentuje podstawowy wskaźnik interfejsu. Użyj <> comptr — zadeklarować zmiennej, a następnie użyć operatora dostępu do elementu członkowskiego strzałkę (`->`) na dostęp do funkcji członkowskiej interfejsu.  
  
 Aby uzyskać więcej informacji na temat wskaźniki inteligentne, zobacz podsekcję "Wskaźniki inteligentne COM" [praktyk kodowania COM](http://msdn.microsoft.com/en-us/76aca556-b4d6-4e67-a2a3-4439900f0c39)tematu w bibliotece MSDN.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Definicje typów publicznych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`InterfaceType`|Synonim dla typu określonego przez `T` parametru szablonu.|  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Comptr::comptr — Konstruktor](../windows/comptr-comptr-constructor.md)|Intializes nowe wystąpienie klasy comptr — klasa. Przeciążenia Podaj konstruktorów domyślnej, copy, przenoszenia i konwersji.|  
|[Comptr —:: ~ ComPtr — destruktor](../windows/comptr-tilde-comptr-destructor.md)|Deinitializes wystąpienia comptr —.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[ComPtr::As — metoda](../windows/comptr-as-method.md)|Zwraca obiekt comptr —, który reprezentuje interfejs identyfikowane przez parametr określonego szablonu.|  
|[ComPtr::AsIID — metoda](../windows/comptr-asiid-method.md)|Zwraca obiekt comptr —, który reprezentuje interfejs identyfikowany przez identyfikator określonego interfejsu.|  
|[ComPtr::AsWeak — metoda](../windows/comptr-asweak-method.md)|Pobiera słabe odwołanie do bieżącego obiektu.|  
|[ComPtr::Attach — metoda](../windows/comptr-attach-method.md)|Kojarzy tego comptr — z typu interfejsu, określony przez parametr typu bieżącego szablonu.|  
|[ComPtr::CopyTo — metoda](../windows/comptr-copyto-method.md)|Kopiuje bieżąca lub określona interfejsu skojarzonego z tym comptr — na wskaźnik określonym produktem wyjściowym.|  
|[ComPtr::Detach — metoda](../windows/comptr-detach-method.md)|Usuwa skojarzenia tego comptr — z interfejsu, który reprezentuje.|  
|[ComPtr::Get — metoda](../windows/comptr-get-method.md)|Pobiera wskaźnik do interfejsu, który jest skojarzony z tym comptr —.|  
|[ComPtr::GetAddressOf — metoda](../windows/comptr-getaddressof-method.md)|Pobiera adres [ptr_ — element](../windows/comptr-ptr-data-member.md) danych elementu członkowskiego, który zawiera wskaźnik do interfejsu reprezentowany przez ten comptr —.|  
|[ComPtr::ReleaseAndGetAddressOf — metoda](../windows/comptr-releaseandgetaddressof-method.md)|Zwalnia skojarzony z tym comptr — interfejs, a następnie pobiera adres [ptr_ — element](../windows/comptr-ptr-data-member.md) danych elementu członkowskiego, który zawiera wskaźnik do interfejsu, która została opublikowana.|  
|[ComPtr::Reset](../windows/comptr-reset.md)|Zwalnia wszystkie odwołania dla wskaźnika interfejsu, który jest skojarzony z tym comptr —.|  
|[ComPtr::Swap — metoda](../windows/comptr-swap-method.md)|Zamienia interfejsu zarządzanych przez bieżący comptr — przy użyciu interfejsu zarządzana przez określony comptr —.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[ComPtr::InternalAddRef — metoda](../windows/comptr-internaladdref-method.md)|Zwiększa liczbę odniesienia skojarzony z tym comptr — interfejs.|  
|[ComPtr::InternalRelease — metoda](../windows/comptr-internalrelease-method.md)|Wykonuje operację wydania COM na skojarzony z tym comptr — interfejs.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[ComPtr::operator Microsoft::WRL::Details::BoolType Operator](../windows/comptr-operator-microsoft-wrl-details-booltype-operator.md)|Wskazuje, czy comptr — Zarządzanie okres istnienia obiektu interfejsu.|  
|[ComPtr::operator — Operator &](../windows/comptr-operator-ampersand-operator.md)|Pobiera adres bieżącej comptr —.|  
|[ComPtr::operator = — Operator](../windows/comptr-operator-assign-operator.md)|Przypisuje wartość do bieżącego comptr —.|  
|[ComPtr::operator -> — Operator](../windows/comptr-operator-arrow-operator.md)|Pobiera wskaźnik do typu określonego przez parametr bieżącego szablonu.|  
|[ComPtr::operator == — Operator](../windows/comptr-operator-equality-operator.md)|Wskazuje, czy dwa obiekty comptr — są takie same.|  
|[ComPtr::operator! = — Operator](../windows/comptr-operator-inequality-operator.md)|Wskazuje, czy dwa obiekty comptr — nie są takie same.|  
  
### <a name="protected-data-members"></a>Dane chronione elementy członkowskie  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Comptr::ptr_ — członek danych](../windows/comptr-ptr-data-member.md)|Zawiera wskaźnik do interfejsu, który jest skojarzony z i zarządzany przez ten comptr —.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `ComPtr`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** client.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::wrl — Namespace](../windows/microsoft-wrl-namespace.md)