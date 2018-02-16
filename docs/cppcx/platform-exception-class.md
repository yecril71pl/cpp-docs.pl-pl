---
title: Klasa platform::Exception | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Exception::Exception
- VCCORLIB/Platform::Exception::CreateException
- VCCORLIB/Platform::Exception::HResult
- VCCORLIB/Platform::Exception::Message
dev_langs:
- C++
helpviewer_keywords:
- Platform::Exception Class
ms.assetid: ca1d5a67-3a5a-48fe-8099-f9c38a2d2dce
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 51df721524fa871b28cc7e4bcb088d4a82a0d1ad
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="platformexception-class"></a>Klasa platform::Exception
Reprezentuje błędów występujących podczas wykonywania aplikacji. Klasy wyjątków niestandardowych nie mogą pochodzić od `Platform::Exception`. Jeśli potrzebujesz niestandardowych wyjątku, można użyć `Platform::COMException` i określić HRESULT specyficzny dla aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
public ref class Exception : Object,    IException,    IPrintable,    IEquatable  
```  
  
### <a name="members"></a>Elementy członkowskie  
 `Exception` Klasa dziedziczy `Object` klasy i `IException`, `IPrintable`, i `IEquatable` interfejsów.  
  
 `Exception` Klasa ma również następujące rodzaje elementów członkowskich.  
  
### <a name="constructors"></a>Konstruktorów  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|[Exception::Exception](#ctor)|Inicjuje nowe wystąpienie klasy `Exception` klasy.|  
  
### <a name="methods"></a>Metody  
 `Exception` Klasa dziedziczy `Equals()`, `Finalize()`,`GetHashCode()`,`GetType()`,`MemberwiseClose()`, i `ToString()` metody [Platform::Object klasy](../cppcx/platform-object-class.md). `Exception` Klasa ma również następujące metody.  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|[Exception::CreateException](#createexception)|Tworzy wyjątek, który reprezentuje określoną wartość HRESULT.|  
  
### <a name="properties"></a>Właściwości  
 Klasy wyjątków ma również następujące właściwości.  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|[Exception::HResult](#hresult)|HRESULT, który odpowiada wyjątek.|  
|[Exception::Message](#message)|Komunikat, który opisuje wyjątek. Ta wartość jest tylko do odczytu i nie można zmodyfikować po `Exception` jest tworzony.|  
  
### <a name="requirements"></a>Wymagania  
 **Minimalna obsługiwana klienta:** systemu Windows 8  
  
 **Minimalna obsługiwana serwera:** systemu Windows Server 2012  
  
 **Namespace:** platformy  
  
 **Metadane:** platform.winmd  

## <a name="createexception"></a> Exception::CreateException — metoda
Tworzy Platform::Exception ^ z określoną wartość HRESULT.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
Exception^ CreateException(int32 hr)  
Exception^ CreateException(int32 hr, Platform::String^ message)  
```  
  
### <a name="parameters"></a>Parametry  
 hr  
 Wartość HRESULT, która zwykle pobrać po wywołaniu metody COM. Jeśli wartość wynosi 0, która jest równa S_OK, ta metoda zgłasza [Platform::InvalidArgumentException](../cppcx/platform-invalidargumentexception-class.md) ponieważ metody modelu COM, które pomyślnie powinien nie zgłaszają wyjątki.  
  
 — komunikat  
 Ciąg opisujący błąd.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wyjątek, który reprezentuje błąd HRESULT.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda umożliwia tworzenie wyjątków poza HRESULT, która jest zwracana, na przykład po wywołaniu metody interfejsu COM. Można użyć przeciążenia, pobierający ciąg ^ parametr, aby podać niestandardowy komunikat.  
  
 Jest zdecydowanie zalecane na potrzeby utworzyć wyjątek jednoznacznie CreateException zamiast tworzenia [Platform::COMException](../cppcx/platform-comexception-class.md) zawiera jedynie HRESULT.  
  


## <a name="ctor"></a>  Konstruktor Exception::Exception
Intializes nowe wystąpienie klasy wyjątku.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
  
Exception(int32 hresult)  
Exception(int32 hresult, ::Platform::String^ message)  
```  
  
### <a name="parameters"></a>Parametry  
 `hresult`  
 Błąd HRESULT reprezentowanego przez wyjątek.  
  
 `message`  
 Komunikat określone przez użytkownika, takie jak przetestowanego tekst, który jest powiązany z wyjątkiem. Ogólnie należy preferowane drugi przeciążenia zapewnić opisowy komunikat, który jest możliwie o metody i przyczyny błędu.  
  


## <a name="hresult"></a>  Właściwość Exception::HResult
HRESULT, który odpowiada wyjątek.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
public:property int HResult {    int get();}  
```  
  
## <a name="property-value"></a>Wartość właściwości  
 Wartość HRESULT.  
  
### <a name="remarks"></a>Uwagi  
 Większość wyjątków uruchamiane jako błędy COM, które są zwracane jako wartości HRESULT. C + +/ CX konwertuje te wartości na Platform::Exception ^ obiektów i ta właściwość przechowuje wartość oryginalny kod błędu.  
  


## <a name="message"></a> Właściwość Exception::Message
Komunikat opisujący błąd.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
public:property String^ Message;  
```  
  
## <a name="property-value"></a>Wartość właściwości  
 W wyjątki, które pochodzą z środowiska uruchomieniowego systemu Windows jest dostarczane przez system opis błędu.  
  
### <a name="remarks"></a>Uwagi  
 W systemie Windows 8 ta właściwość jest tylko do odczytu, ponieważ wyjątki w tej wersji środowiska uruchomieniowego systemu Windows są przenoszone przez ABI tylko jako wyników HRESULT. W Windows 8.1 ABI transport jest bardziej rozbudowane informacje o wyjątku i zapewniają niestandardowy komunikat, który programowo dostęp inne składniki. Aby uzyskać więcej informacji, zobacz [wyjątków (C + +/ CX)](../cppcx/exceptions-c-cx.md).  
  

  
## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw platformy](../cppcx/platform-namespace-c-cx.md)