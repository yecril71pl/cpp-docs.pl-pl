---
title: "Itarget — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ITarget
- AGENTS/concurrency::ITarget
- AGENTS/concurrency::ITarget::propagate
- AGENTS/concurrency::ITarget::send
- AGENTS/concurrency::ITarget::supports_anonymous_source
- AGENTS/concurrency::ITarget::link_source
- AGENTS/concurrency::ITarget::unlink_source
- AGENTS/concurrency::ITarget::unlink_sources
dev_langs: C++
helpviewer_keywords: ITarget class
ms.assetid: 5678db25-112a-4f72-be13-42e16b67c48b
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0b67bf07ed7f1621ceb9a9428a03244ee5661707
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="itarget-class"></a>ITarget — Klasa
`ITarget` Klasy jest interfejs dla wszystkich docelowych bloków. Bloki docelowy korzystać wiadomości oferowane przez `ISource` bloków.  
  
## <a name="syntax"></a>Składnia  
  
```
template<class T>
class ITarget;
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ danych ładunku w wiadomości zaakceptowane przez blok docelowy.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Definicje typów publicznych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`filter_method`|Podpis metody używane przez blok, który zwraca `bool` wartość, aby ustalić, czy wiadomość oferowany powinna być akceptowana.|  
|`type`|Alias typu `T`.|  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[~ ITarget — destruktor](#dtor)|Niszczy `ITarget` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Propagacja](#propagate)|W przypadku przesłonięcia w klasie pochodnej, asynchronicznie przekazuje komunikat z bloku źródłowego do tego bloku docelowego.|  
|[Wyślij](#send)|W przypadku przesłonięcia w klasie pochodnej, synchronicznie przekazuje komunikat do blok docelowy.|  
|[supports_anonymous_source](#supports_anonymous_source)|W przypadku przesłonięcia w klasie pochodnej zwraca wartość PRAWDA lub FAŁSZ w zależności od tego, czy blok komunikatów akceptuje oferowane przez źródło, który nie jest połączony do niego wiadomości. Jeśli zwróci przeciążonej `true`, element docelowy nie mogą odkładać komunikat oferowany jako źródło identyfikację w rejestrze link jej sourse wymaga zużycia przełożonych komunikat w późniejszym czasie.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[link_source](#link_source)|W przypadku przesłonięcia w klasie pochodnej, linki bloku określonego źródła tej `ITarget` bloku.|  
|[unlink_source](#unlink_source)|W przypadku przesłonięcia w klasie pochodnej, odłączenie od tego bloku określonego źródła `ITarget` bloku.|  
|[unlink_sources](#unlink_sources)|W przypadku przesłonięcia w klasie pochodnej, odłączenie wszystkich bloków źródła tego `ITarget` bloku.|  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [bloki komunikatów asynchronicznych](../../../parallel/concrt/asynchronous-message-blocks.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `ITarget`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** agents.h  
  
 **Namespace:** współbieżności  
  
##  <a name="dtor"></a>~ Itarget — 

 Niszczy `ITarget` obiektu.  
  
```
virtual ~ITarget();
```  
  
##  <a name="link_source"></a>link_source 

 W przypadku przesłonięcia w klasie pochodnej, linki bloku określonego źródła tej `ITarget` bloku.  
  
```
virtual void link_source(_Inout_ ISource<T>* _PSource) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `_PSource`  
 `ISource` Zablokować, jest połączone z tym `ITarget` bloku.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja nie powinna być wywoływana bezpośrednio na `ITarget` bloku. Bloki powinny być połączone ze sobą przy użyciu `link_target` metoda `ISource` bloków, które wywoła `link_source` metody w celu odpowiedniego.  
  
##  <a name="propagate"></a>Propagacja 

 W przypadku przesłonięcia w klasie pochodnej, asynchronicznie przekazuje komunikat z bloku źródłowego do tego bloku docelowego.  
  
```
virtual message_status propagate(
    _Inout_opt_ message<T>* _PMessage,
    _Inout_opt_ ISource<T>* _PSource) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `_PMessage`  
 Wskaźnik do `message` obiektu.  
  
 `_PSource`  
 Wskaźnik do bloku źródłowego oferty wiadomości.  
  
### <a name="return-value"></a>Wartość zwracana  
 A [message_status —](concurrency-namespace-enums.md) wskazanie docelowy korzystam z komunikatu.  
  
### <a name="remarks"></a>Uwagi  
 Metoda zgłasza [invalid_argument —](../../../standard-library/invalid-argument-class.md) wyjątek, jeśli dowolny `_PMessage` lub `_PSource` parametr jest `NULL`.  
  
##  <a name="send"></a>Wyślij 

 W przypadku przesłonięcia w klasie pochodnej, synchronicznie przekazuje komunikat do blok docelowy.  
  
```
virtual message_status send(
    _Inout_ message<T>* _PMessage,
    _Inout_ ISource<T>* _PSource) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `_PMessage`  
 Wskaźnik do `message` obiektu.  
  
 `_PSource`  
 Wskaźnik do bloku źródłowego oferty wiadomości.  
  
### <a name="return-value"></a>Wartość zwracana  
 A [message_status —](concurrency-namespace-enums.md) wskazanie docelowy korzystam z komunikatu.  
  
### <a name="remarks"></a>Uwagi  
 Metoda zgłasza [invalid_argument —](../../../standard-library/invalid-argument-class.md) wyjątek, jeśli dowolny `_PMessage` lub `_PSource` parametr jest `NULL`.  
  
 Przy użyciu `send` metody poza inicjowania wiadomości oraz propagację wiadomości w sieci jest niebezpieczny i może doprowadzić do zakleszczenia.  
  
 Gdy `send` zwraca komunikat albo już zostało zaakceptowane i przesyłane do bloku docelowego lub została odrzucona przez element docelowy.  
  
##  <a name="supports_anonymous_source"></a>supports_anonymous_source 

 W przypadku przesłonięcia w klasie pochodnej zwraca wartość PRAWDA lub FAŁSZ w zależności od tego, czy blok komunikatów akceptuje oferowane przez źródło, który nie jest połączony do niego wiadomości. Jeśli zwróci przeciążonej `true`, element docelowy nie mogą odkładać komunikat oferowany jako źródło identyfikację w rejestrze link jej sourse wymaga zużycia przełożonych komunikat w późniejszym czasie.  
  
```
virtual bool supports_anonymous_source();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli blok może zaakceptować komunikatów ze źródła, która nie jest połączona z jej `false` inaczej.  
  
##  <a name="unlink_source"></a>unlink_source 

 W przypadku przesłonięcia w klasie pochodnej, odłączenie od tego bloku określonego źródła `ITarget` bloku.  
  
```
virtual void unlink_source(_Inout_ ISource<T>* _PSource) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `_PSource`  
 `ISource` Zablokować, jest rozłączony z tego `ITarget` bloku.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja nie powinna być wywoływana bezpośrednio na `ITarget` bloku. Bloki musi być odłączony przy użyciu `unlink_target` lub `unlink_targets` metod `ISource` bloków, które wywoła `unlink_source` metody w celu odpowiedniego.  
  
##  <a name="unlink_sources"></a>unlink_sources 

 W przypadku przesłonięcia w klasie pochodnej, odłączenie wszystkich bloków źródła tego `ITarget` bloku.  
  
```
virtual void unlink_sources() = 0;
```  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność Namespace](concurrency-namespace.md)   
 [ISource, klasa](isource-class.md)
