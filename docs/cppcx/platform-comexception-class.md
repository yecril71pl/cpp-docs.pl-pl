---
title: Klasa platform::COMException | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- VCCORLIB/Platform::COMException
- VCCORLIB/Platform::Exception::HResult
- VCCORLIB/Platform::Exception::Message
dev_langs: C++
helpviewer_keywords: Platform::COMException Class
ms.assetid: 44fda4e5-574f-4d12-ab5f-4ff3f277448d
caps.latest.revision: "4"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: 28475df3c5d13d1b90483213173f5343f6b85d79
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="platformcomexception-class"></a>Klasa platform::COMException
Reprezentuje COM o błędach podczas wykonywania aplikacji. COMException jest klasą bazową dla zestawu wstępnie zdefiniowanych, standard wyjątków.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
public ref class COMException : Exception,    IException,    IPrintable,    IEquatable  
```  
  
### <a name="members"></a>Elementy członkowskie  
 COMException, klasa dziedziczy z klasy i interfejsy IException, IPrintable i interfejsu IEquatable.  
  
 COMException ma również następujące typy elementów członkowskich.  
  
 **Konstruktory**  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|[COMException](#ctor)|Inicjuje nowe wystąpienie klasy COMException.|  
  
 **Metody**  
  
 COMException, klasa dziedziczy z metody metodę Equals, Finalize() metoda GetHashCode(), GetType(), MemberwiseClose() i ToString() [Platform::Object klasy](../cppcx/platform-object-class.md).  
  
 **Właściwości**  
  
 COMException, klasa ma następujące właściwości.  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|[Exception::HResult](#hresult)|HRESULT, który odpowiada wyjątek.|  
|[Exception::Message](#message)|Komunikat opisujący wyjątek.|  
  
## <a name="derived-exceptions"></a>Pochodne wyjątków  
 Następujące wstępnie zdefiniowane wyjątki są uzyskiwane z COMException. Są one różne od COMException tylko w ich nazw, nazwy ich Konstruktor i ich odpowiednia wartość HRESULT.  
  
|Nazwa|Bazowy HRESULT|Opis|  
|----------|------------------------|-----------------|  
|COMException|*hresult zdefiniowane przez użytkownika*|Element zgłaszany, gdy nierozpoznany HRESULT jest zwracana z wywołania metody COM.|  
|AccessDeniedException|E_ACCESSDENIED|Element zgłaszany, gdy odmowa dostępu do zasobów lub funkcji.|  
|ChangedStateException|E_CHANGED_STATE|Element zgłaszany, gdy metody iterator kolekcji lub tego widoku kolekcji są wywoływane po zmianie kolekcji nadrzędnej, unieważnia wyniki metody.|  
|ClassNotRegisteredException|REGDB_E_CLASSNOTREG|Element zgłaszany, gdy klasa COM nie został zarejestrowany.|  
|DisconnectedException|RPC_E_DISCONNECTED|Element zgłaszany, gdy obiekt jest odłączony od klientów.|  
|FailureException|E_FAIL|Element zgłaszany, gdy operacja nie powiedzie się.|  
|InvalidArgumentException|E_INVALIDARG|Element zgłaszany, gdy jedna z podanych argumentów metody jest nieprawidłowa.|  
|Invalidcastexception —|E_NOINTERFACE|Element zgłaszany, gdy nie można rzutować typu do innego typu.|  
|Notimplementedexception —|E_NOTIMPL|Element zgłaszany, gdy metoda interfejsu nie została zaimplementowana w klasie.|  
|NullReferenceException|E_POINTER|Element zgłaszany, gdy jest próba wyłuskania odwołanie do obiektu o wartości null.|  
|Operationcanceledexception —|E_ABORT|Element zgłaszany, gdy operacja została przerwana.|  
|OutOfBoundsException|E_BOUNDS|Element zgłaszany, gdy operacja próbuje uzyskać dostęp do danych poza prawidłowym zakresem.|  
|OutOfMemoryException|E_OUTOFMEMORY|Element zgłaszany, gdy jest za mało pamięci do ukończenia tej operacji.|  
  
### <a name="requirements"></a>Wymagania  
 **Minimalna obsługiwana klienta:** systemu Windows 8  
  
 **Minimalna obsługiwana serwera:** systemu Windows Server 2012  
  
 **Namespace:** platformy  
  
 **Metadane:** platform.winmd  

## <a name="ctor"></a>Konstruktor COMException::COMException
Intializes nowe wystąpienie klasy COMException.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
COMException( int hresult )  
```  
  
### <a name="parameters"></a>Parametry  
 HRESULT  
 Błąd HRESULT reprezentowanego przez wyjątek.  
  


## <a name="hresult"></a>Właściwość COMException::HResult
HRESULT, który odpowiada wyjątek.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
public:property int HResult {    int get();}  
```  
  
## <a name="property-value"></a>Wartość właściwości  
 Wartość HRESULT, która określa błędu.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji dotyczących sposobu interpretowania wartość HRESULT, zobacz [struktury COM kody błędów](http://go.microsoft.com/fwlink/p/?LinkId=262045).  

## <a name="message"></a>Właściwość COMException::Message
Komunikat opisujący wyjątek.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
public:property String^ Message {    String^ get();}  
```  
  
### <a name="property-value"></a>Wartość właściwości  
 Opis wyjątku.  
    

## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw platformy](../cppcx/platform-namespace-c-cx.md)