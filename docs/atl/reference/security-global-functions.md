---
title: Funkcje globalne zabezpieczeń | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 053e7adb5a0f5d6c65f599ae694525853bd221a7
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43211794"
---
# <a name="security-global-functions"></a>Funkcje globalne zabezpieczeń
Te funkcje zapewniają obsługę modyfikowanie obiektów SID i listy ACL.  
  
> [!IMPORTANT]
>  Funkcje wymienione w poniższej tabeli nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.  
  
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
>  Ta funkcja nie może służyć w aplikacjach korzystających ze środowiska wykonawczego Windows.  
  
```
inline bool AtlGetDacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CDacl* pDacl) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *hObject*  
 Uchwytu do obiektu, dla którego mają zostać pobrane informacje o zabezpieczeniach.  
  
 *Typ obiektu*  
 Określa wartość z zakresu od [SE_OBJECT_TYPE](/windows/desktop/api/accctrl/ne-accctrl-_se_object_type) wyliczenie, które wskazuje typ obiektu identyfikowane przez *hObject* parametru.  
  
 *pDacl*  
 Wskaźnik do obiektu DACL, który będzie zawierać informacji o zabezpieczeniach pobrane.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 W kompilacjach debugowania, wystąpi błąd asercji Jeśli *hObject* lub *pDacl* jest nieprawidłowy.  
  
##  <a name="atlsetdacl"></a>  AtlSetDacl  
 Wywołaj tę funkcję, aby ustawić informacje o poufnej liście kontroli dostępu (DACL) określonego obiektu.  
  
> [!IMPORTANT]
>  Ta funkcja nie może służyć w aplikacjach korzystających ze środowiska wykonawczego Windows.  
  
```
inline bool AtlSetDacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CDacl& rDacl,
    DWORD dwInheritanceFlowControl = 0) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 *hObject*  
 Uchwytu do obiektu, dla której chcesz ustawić informacje o zabezpieczeniach.  
  
 *Typ obiektu*  
 Określa wartość z zakresu od [SE_OBJECT_TYPE](/windows/desktop/api/accctrl/ne-accctrl-_se_object_type) wyliczenie, które wskazuje typ obiektu identyfikowane przez *hObject* parametru.  
  
 *rDacl*  
 Lista DACL zawierającego nowe informacje o zabezpieczeniach.  
  
 *dwInheritanceFlowControl*  
 Sterowanie przepływem dziedziczenia. Ta wartość może być 0 (domyślnie), PROTECTED_DACL_SECURITY_INFORMATION lub UNPROTECTED_DACL_SECURITY_INFORMATION.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 W kompilacjach debugowania, wystąpi błąd asercji Jeśli *hObject* jest nieprawidłowa lub jeśli *dwInheritanceFlowControl* nie jest jednym z trzech wartości dozwolonych.  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlsecurity.h 

##  <a name="atlgetgroupsid"></a>  AtlGetGroupSid  
 Wywołaj tę funkcję, aby pobrać identyfikator zabezpieczeń grupy (SID) obiektu.  
  
> [!IMPORTANT]
>  Ta funkcja nie może służyć w aplikacjach korzystających ze środowiska wykonawczego Windows.  
  
```
inline bool AtlGetGroupSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CSid* pSid) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 *hObject*  
 Uchwytu do obiektu, z którego można pobrać informacji o zabezpieczeniach.  
  
 *Typ obiektu*  
 Określa wartość z zakresu od [SE_OBJECT_TYPE](/windows/desktop/api/accctrl/ne-accctrl-_se_object_type) wyliczenie, które wskazuje typ obiektu identyfikowane przez *hObject* parametru.  
  
 *pSid*  
 Wskaźnik do `CSid` obiektu, który będzie zawierać nowe informacje o zabezpieczeniach.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlsecurity.h 

##  <a name="atlsetgroupsid"></a>  AtlSetGroupSid  
 Wywołaj tę funkcję, aby ustawić identyfikator zabezpieczeń grupy (SID) obiektu.  
  
> [!IMPORTANT]
>  Ta funkcja nie może służyć w aplikacjach korzystających ze środowiska wykonawczego Windows.  
  
```
inline bool AtlSetGroupSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CSid& rSid) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 *hObject*  
 Uchwytu do obiektu, dla której chcesz ustawić informacje o zabezpieczeniach.  
  
 *Typ obiektu*  
 Określa wartość z zakresu od [SE_OBJECT_TYPE](/windows/desktop/api/accctrl/ne-accctrl-_se_object_type) wyliczenie, które wskazuje typ obiektu identyfikowane przez *hObject* parametru.  
  
 *rSid*  
 `CSid` Obiektu zawierającego nowe informacje o zabezpieczeniach.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlsecurity.h 

##  <a name="atlgetownersid"></a>  AtlGetOwnerSid  
 Wywołaj tę funkcję, aby pobrać identyfikator zabezpieczeń właściciela (SID) obiektu.  
  
> [!IMPORTANT]
>  Ta funkcja nie może służyć w aplikacjach korzystających ze środowiska wykonawczego Windows.  
  
```
inline bool AtlGetOwnerSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CSid* pSid) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 *hObject*  
 Uchwytu do obiektu, z którego można pobrać informacji o zabezpieczeniach.  
  
 *Typ obiektu*  
 Określa wartość z zakresu od [SE_OBJECT_TYPE](/windows/desktop/api/accctrl/ne-accctrl-_se_object_type) wyliczenie, które wskazuje typ obiektu identyfikowane przez *hObject* parametru.  
  
 *pSid*  
 Wskaźnik do `CSid` obiektu, który będzie zawierać nowe informacje o zabezpieczeniach.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlsecurity.h 

##  <a name="atlsetownersid"></a>  AtlSetOwnerSid  
 Wywołaj tę funkcję, aby ustawić identyfikator zabezpieczeń właściciela (SID) obiektu.  
  
> [!IMPORTANT]
>  Ta funkcja nie może służyć w aplikacjach korzystających ze środowiska wykonawczego Windows.  
  
```
inline bool AtlSetOwnerSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CSid& rSid) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 *hObject*  
 Uchwytu do obiektu, dla której chcesz ustawić informacje o zabezpieczeniach.  
  
 *Typ obiektu*  
 Określa wartość z zakresu od [SE_OBJECT_TYPE](/windows/desktop/api/accctrl/ne-accctrl-_se_object_type) wyliczenie, które wskazuje typ obiektu identyfikowane przez *hObject* parametru.  
  
 *rSid*  
 `CSid` Obiektu zawierającego nowe informacje o zabezpieczeniach.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlsecurity.h 

##  <a name="atlgetsacl"></a>  AtlGetSacl  
 Wywołaj tę funkcję, aby pobrać informacje o systemowej liście kontroli dostępu (SACL) określonego obiektu.  
  
> [!IMPORTANT]
>  Ta funkcja nie może służyć w aplikacjach korzystających ze środowiska wykonawczego Windows.  
  
```
inline bool AtlGetSacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CSacl* pSacl,
    bool bRequestNeededPrivileges = true) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 *hObject*  
 Uchwytu do obiektu, z którego można pobrać informacji o zabezpieczeniach.  
  
 *Typ obiektu*  
 Określa wartość z zakresu od [SE_OBJECT_TYPE](/windows/desktop/api/accctrl/ne-accctrl-_se_object_type) wyliczenie, które wskazuje typ obiektu identyfikowane przez *hObject* parametru.  
  
 *pSacl*  
 Wskaźnik do obiektu SACL, który będzie zawierać informacji o zabezpieczeniach pobrane.  
  
 *bRequestNeededPrivileges*  
 W przypadku opcji true funkcja będzie podejmować próby włączenia uprawnień SE_SECURITY_NAME i przywrócić ją po zakończeniu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `AtlGetSacl` jest wywoływana wiele razy na wiele różnych obiektów, będzie bardziej wydajne, aby włączyć uprawnienia SE_SECURITY_NAME raz przed wywołaniem funkcji, z *bRequestNeededPrivileges* ustawiony na wartość false.  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlsecurity.h 

##  <a name="atlsetsacl"></a>  AtlSetSacl  
 Wywołaj tę funkcję, aby ustawić informacje o systemowej liście kontroli dostępu (SACL) określonego obiektu.  
  
> [!IMPORTANT]
>  Ta funkcja nie może służyć w aplikacjach korzystających ze środowiska wykonawczego Windows.  
  
```
inline bool AtlSetSacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CSacl& rSacl,
    DWORD dwInheritanceFlowControl = 0,
    bool bRequestNeededPrivileges = true) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 *hObject*  
 Uchwytu do obiektu, dla której chcesz ustawić informacje o zabezpieczeniach.  
  
 *Typ obiektu*  
 Określa wartość z zakresu od [SE_OBJECT_TYPE](/windows/desktop/api/accctrl/ne-accctrl-_se_object_type) wyliczenie, które wskazuje typ obiektu identyfikowane przez *hObject* parametru.  
  
 *rSacl*  
 SACL, zawierającego nowe informacje o zabezpieczeniach.  
  
 *dwInheritanceFlowControl*  
 Sterowanie przepływem dziedziczenia. Ta wartość może być 0 (domyślnie), PROTECTED_SACL_SECURITY_INFORMATION lub UNPROTECTED_SACL_SECURITY_INFORMATION.  
  
 *bRequestNeededPrivileges*  
 W przypadku opcji true funkcja będzie podejmować próby włączenia uprawnień SE_SECURITY_NAME i przywrócić ją po zakończeniu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 W kompilacjach debugowania, wystąpi błąd asercji Jeśli *hObject* jest nieprawidłowa lub jeśli *dwInheritanceFlowControl* nie jest jednym z trzech wartości dozwolonych.  
  
 Jeśli `AtlSetSacl` jest wywoływana wiele razy na wiele różnych obiektów, będzie bardziej wydajne, aby włączyć uprawnienia SE_SECURITY_NAME raz przed wywołaniem funkcji, z *bRequestNeededPrivileges* ustawiony na wartość false.  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlsecurity.h 

##  <a name="atlgetsecuritydescriptor"></a>  AtlGetSecurityDescriptor  
 Wywołaj tę funkcję, aby pobrać deskryptor zabezpieczeń danego obiektu.  
  
> [!IMPORTANT]
>  Ta funkcja nie może służyć w aplikacjach korzystających ze środowiska wykonawczego Windows.  
  
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
 Wskaźnik na ciąg zakończony znakiem null, który określa nazwę obiektu, z którego można pobrać informacji o zabezpieczeniach.  
  
 *Typ obiektu*  
 Określa wartość z zakresu od [SE_OBJECT_TYPE](/windows/desktop/api/accctrl/ne-accctrl-_se_object_type) wyliczenie, które wskazuje typ obiektu identyfikowane przez *pszObjectName* parametru.  
  
 *pSecurityDescriptor*  
 Obiekt, który odbiera deskryptora zabezpieczeń żądanej.  
  
 *requestedInfo*  
 Zbiór [SECURITY_INFORMATION](/windows/desktop/SecAuthZ/security-information) bit flagi wskazujące rodzaj informacji o zabezpieczeniach do pobrania. Ten parametr może być kombinacją następujących wartości.  
  
 *bRequestNeededPrivileges*  
 W przypadku opcji true funkcja będzie podejmować próby włączenia uprawnień SE_SECURITY_NAME i przywrócić ją po zakończeniu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `AtlGetSecurityDescriptor` jest wywoływana wiele razy na wiele różnych obiektów, będzie bardziej wydajne, aby włączyć uprawnienia SE_SECURITY_NAME raz przed wywołaniem funkcji, z *bRequestNeededPrivileges* ustawiony na wartość false.  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlsecurity.h 
   
## <a name="see-also"></a>Zobacz też  
 [Funkcje](../../atl/reference/atl-functions.md)
