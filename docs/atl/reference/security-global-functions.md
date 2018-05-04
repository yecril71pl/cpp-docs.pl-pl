---
title: Globalne funkcje zabezpieczeń | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlsecurity/ATL::AtlGetDacl
- atlsecurity/ATL::AtlSetDacl
- atlsecurity/ATL::AtlGetGroupSid
- atlsecurity/ATL::AtlSetGroupSid
- atlsecurity/ATL::AtlGetOwnerSid
- atlsecurity/ATL::AtlSetOwnerSid
- atlsecurity/ATL::AtlGetSacl
- atlsecurity/ATL::AtlSetSacl
- atlsecurity/ATL::AtlGetSecurityDescriptor
dev_langs:
- C++
helpviewer_keywords:
- SIDs [C++], modifying SID objects
- ACL object global functions
- security IDs [C++]
ms.assetid: 6a584bfe-16b7-47f4-8439-9c789c41567a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ad9ad170706b72c9d236e095db0e2b6df00031ff
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="security-global-functions"></a>Globalne funkcje zabezpieczeń
Funkcje te zapewniają obsługę modyfikowanie obiektów identyfikator SID i listy kontroli dostępu.  
  
> [!IMPORTANT]
>  Funkcje wymienione w poniższej tabeli nie można używać w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
|||  
|-|-|  
|[AtlGetDacl](#atlgetdacl)|Wywołaj tę funkcję, aby pobrać informacje o poufnej liście kontroli dostępu (DACL) określonego obiektu.|  
|[AtlSetDacl](#atlsetdacl)|Wywołaj tę funkcję, aby ustawić informacje o poufnej liście kontroli dostępu (DACL) określonego obiektu.|  
|[AtlGetGroupSid](#atlgetgroupsid)|Wywołaj tę funkcję, aby pobrać identyfikator zabezpieczeń grupy (SID) obiektu.|  
|[AtlSetGroupSid](#atlsetgroupsid)|Wywołaj tę funkcję, aby ustawić identyfikator zabezpieczeń grupy (SID) obiektu.|  
|[AtlGetOwnerSid](#atlgetownersid)|Wywołaj tę funkcję, aby pobrać identyfikator zabezpieczeń właściciela (SID) obiektu.|  
|[AtlSetOwnerSid](#atlsetownersid)|Wywołaj tę funkcję, aby ustawić identyfikator zabezpieczeń właściciela (SID) obiektu.|  
|[AtlGetSacl](#atlgetsacl)|Wywołaj tę funkcję, aby pobrać informacje o systemowej liście kontroli dostępu (SACL) określonego obiektu.|  
|[AtlSetSacl](#atlsetsacl)|Wywołaj tę funkcję, aby ustawić informacje o systemowej liście kontroli dostępu (SACL) określonego obiektu.|  
|[AtlGetSecurityDescriptor](#atlgetsecuritydescriptor)|Wywołaj tę funkcję, aby pobrać deskryptor zabezpieczeń danego obiektu.|  

## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlsecurity.h 

##  <a name="atlgetdacl"></a>  AtlGetDacl  
 Wywołaj tę funkcję, aby pobrać informacje o poufnej liście kontroli dostępu (DACL) określonego obiektu.  
  
> [!IMPORTANT]
>  Nie można użyć tej funkcji w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
```
inline bool AtlGetDacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CDacl* pDacl) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `hObject`  
 Dojście do obiektu, który można pobrać informacji o zabezpieczeniach.  
  
 `ObjectType`  
 Określa wartość z zakresu od [SE_OBJECT_TYPE](http://msdn.microsoft.com/library/windows/desktop/aa379593) wyliczenia wskazująca typ obiektu identyfikowane przez `hObject` parametru.  
  
 `pDacl`  
 Wskaźnik do obiektu listy DACL, który będzie zawierać informacje o zabezpieczeniach pobrane.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 W kompilacjach debugowania, wystąpi błąd potwierdzenia Jeśli `hObject` lub `pDacl` jest nieprawidłowy.  
  
##  <a name="atlsetdacl"></a>  AtlSetDacl  
 Wywołaj tę funkcję, aby ustawić informacje o poufnej liście kontroli dostępu (DACL) określonego obiektu.  
  
> [!IMPORTANT]
>  Nie można użyć tej funkcji w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
```
inline bool AtlSetDacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CDacl& rDacl,
    DWORD dwInheritanceFlowControl = 0) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `hObject`  
 Dojście do obiektu, do których chcesz ustawić informacji zabezpieczeń.  
  
 `ObjectType`  
 Określa wartość z zakresu od [SE_OBJECT_TYPE](http://msdn.microsoft.com/library/windows/desktop/aa379593) wyliczenia wskazująca typ obiektu identyfikowane przez `hObject` parametru.  
  
 `rDacl`  
 Lista DACL zawierającego nowe informacje o zabezpieczeniach.  
  
 `dwInheritanceFlowControl`  
 Sterowanie przepływem dziedziczenia. Ta wartość może być 0 (domyślnie), PROTECTED_DACL_SECURITY_INFORMATION lub UNPROTECTED_DACL_SECURITY_INFORMATION.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 W kompilacjach debugowania, wystąpi błąd potwierdzenia Jeśli `hObject` jest nieprawidłowy, lub jeśli `dwInheritanceFlowControl` nie jest jednym z trzech wartości dozwolonych.  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlsecurity.h 

##  <a name="atlgetgroupsid"></a>  AtlGetGroupSid  
 Wywołaj tę funkcję, aby pobrać identyfikator zabezpieczeń grupy (SID) obiektu.  
  
> [!IMPORTANT]
>  Nie można użyć tej funkcji w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
```
inline bool AtlGetGroupSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CSid* pSid) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `hObject`  
 Dojście do obiektu, z którego można pobrać informacji o zabezpieczeniach.  
  
 `ObjectType`  
 Określa wartość z zakresu od [SE_OBJECT_TYPE](http://msdn.microsoft.com/library/windows/desktop/aa379593) wyliczenia wskazująca typ obiektu identyfikowane przez `hObject` parametru.  
  
 `pSid`  
 Wskaźnik do `CSid` obiektu, który będzie zawierać nowych informacji o zabezpieczeniach.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlsecurity.h 

##  <a name="atlsetgroupsid"></a>  AtlSetGroupSid  
 Wywołaj tę funkcję, aby ustawić identyfikator zabezpieczeń grupy (SID) obiektu.  
  
> [!IMPORTANT]
>  Nie można użyć tej funkcji w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
```
inline bool AtlSetGroupSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CSid& rSid) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `hObject`  
 Dojście do obiektu, do których chcesz ustawić informacji zabezpieczeń.  
  
 `ObjectType`  
 Określa wartość z zakresu od [SE_OBJECT_TYPE](http://msdn.microsoft.com/library/windows/desktop/aa379593) wyliczenia wskazująca typ obiektu identyfikowane przez `hObject` parametru.  
  
 `rSid`  
 `CSid` Obiektu zawierającego nowe informacje o zabezpieczeniach.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlsecurity.h 

##  <a name="atlgetownersid"></a>  AtlGetOwnerSid  
 Wywołaj tę funkcję, aby pobrać identyfikator zabezpieczeń właściciela (SID) obiektu.  
  
> [!IMPORTANT]
>  Nie można użyć tej funkcji w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
```
inline bool AtlGetOwnerSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CSid* pSid) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `hObject`  
 Dojście do obiektu, z którego można pobrać informacji o zabezpieczeniach.  
  
 `ObjectType`  
 Określa wartość z zakresu od [SE_OBJECT_TYPE](http://msdn.microsoft.com/library/windows/desktop/aa379593) wyliczenia wskazująca typ obiektu identyfikowane przez `hObject` parametru.  
  
 `pSid`  
 Wskaźnik do `CSid` obiektu, który będzie zawierać nowych informacji o zabezpieczeniach.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlsecurity.h 

##  <a name="atlsetownersid"></a>  AtlSetOwnerSid  
 Wywołaj tę funkcję, aby ustawić identyfikator zabezpieczeń właściciela (SID) obiektu.  
  
> [!IMPORTANT]
>  Nie można użyć tej funkcji w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
```
inline bool AtlSetOwnerSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CSid& rSid) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `hObject`  
 Dojście do obiektu, do których chcesz ustawić informacji zabezpieczeń.  
  
 `ObjectType`  
 Określa wartość z zakresu od [SE_OBJECT_TYPE](http://msdn.microsoft.com/library/windows/desktop/aa379593) wyliczenia wskazująca typ obiektu identyfikowane przez `hObject` parametru.  
  
 `rSid`  
 `CSid` Obiektu zawierającego nowe informacje o zabezpieczeniach.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlsecurity.h 

##  <a name="atlgetsacl"></a>  AtlGetSacl  
 Wywołaj tę funkcję, aby pobrać informacje o systemowej liście kontroli dostępu (SACL) określonego obiektu.  
  
> [!IMPORTANT]
>  Nie można użyć tej funkcji w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
```
inline bool AtlGetSacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CSacl* pSacl,
    bool bRequestNeededPrivileges = true) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `hObject`  
 Dojście do obiektu, z którego można pobrać informacji o zabezpieczeniach.  
  
 `ObjectType`  
 Określa wartość z zakresu od [SE_OBJECT_TYPE](http://msdn.microsoft.com/library/windows/desktop/aa379593) wyliczenia wskazująca typ obiektu identyfikowane przez `hObject` parametru.  
  
 `pSacl`  
 Wskaźnik do obiektu SACL, który będzie zawierać informacje o zabezpieczeniach pobrane.  
  
 `bRequestNeededPrivileges`  
 Jeśli PRAWDA, funkcja podejmie próbę włączenia uprawnień SE_SECURITY_NAME i przywróć ją po zakończeniu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `AtlGetSacl` jest wywoływana wiele razy na wiele różnych obiektów, będzie bardziej wydajne, aby włączyć uprawnień SE_SECURITY_NAME raz, przed wywołaniem funkcji, z `bRequestNeededPrivileges` ustawiony na wartość false.  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlsecurity.h 

##  <a name="atlsetsacl"></a>  AtlSetSacl  
 Wywołaj tę funkcję, aby ustawić informacje o systemowej liście kontroli dostępu (SACL) określonego obiektu.  
  
> [!IMPORTANT]
>  Nie można użyć tej funkcji w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
```
inline bool AtlSetSacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CSacl& rSacl,
    DWORD dwInheritanceFlowControl = 0,
    bool bRequestNeededPrivileges = true) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `hObject`  
 Dojście do obiektu, do których chcesz ustawić informacji zabezpieczeń.  
  
 `ObjectType`  
 Określa wartość z zakresu od [SE_OBJECT_TYPE](http://msdn.microsoft.com/library/windows/desktop/aa379593) wyliczenia wskazująca typ obiektu identyfikowane przez `hObject` parametru.  
  
 *rSacl*  
 Lista SACL zawierającego nowe informacje o zabezpieczeniach.  
  
 `dwInheritanceFlowControl`  
 Sterowanie przepływem dziedziczenia. Ta wartość może być 0 (domyślnie), PROTECTED_SACL_SECURITY_INFORMATION lub UNPROTECTED_SACL_SECURITY_INFORMATION.  
  
 `bRequestNeededPrivileges`  
 Jeśli PRAWDA, funkcja podejmie próbę włączenia uprawnień SE_SECURITY_NAME i przywróć ją po zakończeniu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 W kompilacjach debugowania, wystąpi błąd potwierdzenia Jeśli `hObject` jest nieprawidłowy, lub jeśli `dwInheritanceFlowControl` nie jest jednym z trzech wartości dozwolonych.  
  
 Jeśli `AtlSetSacl` jest wywoływana wiele razy na wiele różnych obiektów, będzie bardziej wydajne, aby włączyć uprawnień SE_SECURITY_NAME raz, przed wywołaniem funkcji, z `bRequestNeededPrivileges` ustawiony na wartość false.  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlsecurity.h 

##  <a name="atlgetsecuritydescriptor"></a>  AtlGetSecurityDescriptor  
 Wywołaj tę funkcję, aby pobrać deskryptor zabezpieczeń danego obiektu.  
  
> [!IMPORTANT]
>  Nie można użyć tej funkcji w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
```
inline bool AtlGetSecurityDescriptor(
    LPCTSTR pszObjectName,
    SE_OBJECT_TYPE ObjectType,
    CSecurityDesc* pSecurityDescriptor,
    SECURITY_INFORMATION requestedInfo = OWNER_SECURITY_INFORMATION |
    GROUP_SECURITY_INFORMATION | DACL_SECURITY_INFORMATION |
    SACL_SECURITY_INFORMATION,
 bool bRequestNeededPrivileges = true) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 *pszObjectName*  
 Wskaźnik do zerem ciąg, który określa nazwę obiektu, z którego można pobrać informacji o zabezpieczeniach.  
  
 `ObjectType`  
 Określa wartość z zakresu od [SE_OBJECT_TYPE](http://msdn.microsoft.com/library/windows/desktop/aa379593) wyliczenia wskazująca typ obiektu identyfikowane przez *pszObjectName* parametru.  
  
 *pSecurityDescriptor*  
 Obiekt, który odbiera deskryptora zabezpieczeń żądanej.  
  
 *requestedInfo*  
 Zestaw [SECURITY_INFORMATION](http://msdn.microsoft.com/library/windows/desktop/aa379573) bit flagi, które określają typ informacji o zabezpieczeniach do pobrania. Ten parametr może być kombinacją następujących wartości.  
  
 `bRequestNeededPrivileges`  
 Jeśli PRAWDA, funkcja podejmie próbę włączenia uprawnień SE_SECURITY_NAME i przywróć ją po zakończeniu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `AtlGetSecurityDescriptor` jest wywoływana wiele razy na wiele różnych obiektów, będzie bardziej wydajne, aby włączyć uprawnień SE_SECURITY_NAME raz, przed wywołaniem funkcji, z `bRequestNeededPrivileges` ustawiony na wartość false.  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlsecurity.h 
   
## <a name="see-also"></a>Zobacz też  
 [Funkcje](../../atl/reference/atl-functions.md)
