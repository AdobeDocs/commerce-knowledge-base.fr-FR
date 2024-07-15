---
title: Dépréciation des intégrations des paiements Adobe Commerce de base
description: En raison du PSD 2 de la directive sur les services de paiement (voir les détails de la [directive sur les services de paiement](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/payments/compliance-payment-services-directive.html) dans notre guide d’utilisation) et de l’évolution continue de nombreuses API, un certain nombre d’intégrations des paiements de base d’Adobe Commerce risquent de devenir obsolètes et de ne plus être compatibles avec la sécurité à l’avenir. À cette fin, de nombreuses intégrations de paiement de base ont été ou seront bientôt obsolètes, et nous recommandons une transition vers leurs extensions de Commerce Marketplace correspondantes. Veuillez lire le reste de l’article ci-dessous pour examiner les récentes obsolescences des intégrations de paiement. Chacun des liens **Status** se trouve dans notre guide d’utilisation. **Les intégrations ci-dessous seront toutes supprimées de la version 2.4.0 d’Adobe Commerce et ont été abandonnées à partir des versions 2.3.**
exl-id: c2c4b3b6-409d-466f-a4f3-dfe13ac7f972
feature: Compliance, Integration
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '570'
ht-degree: 0%

---

# Dépréciation des intégrations des paiements Adobe Commerce de base

En raison du PSD 2 de la directive sur les services de paiement (voir les détails de la [directive sur les services de paiement](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/payments/compliance-payment-services-directive.html) dans notre guide d’utilisation) et de l’évolution continue de nombreuses API, un certain nombre d’intégrations de paiement de base d’Adobe Commerce risquent de devenir obsolètes et de ne plus être compatibles avec la sécurité à l’avenir. À cette fin, de nombreuses intégrations de paiement de base ont été ou seront bientôt obsolètes, et nous recommandons une transition vers leurs extensions de Commerce Marketplace correspondantes. Veuillez lire le reste de l’article ci-dessous pour examiner les récentes obsolescences des intégrations de paiement. Chacun des liens **Status** figure dans notre guide de l’utilisateur. **Les intégrations ci-dessous seront toutes supprimées de la version 2.4.0 d’Adobe Commerce et ont été abandonnées à partir des versions 2.3.**

<table style="height: 243px;" width="712">
<tbody>
<tr>
<td style="width: 225.455px;"><strong>Intégration de méthodes de paiement</strong></td>
<td style="width: 226.364px;"><strong>État</strong></td>
<td style="width: 226.364px;"><strong>Recommandation Adobe Commerce 2.X</strong></td>
</tr>
<tr>
<td style="width: 225.455px;">Worldpay</td>
<td style="width: 226.364px;">2.3.x - <a href="https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html?lang=en#recommended-solutions">Obsolète depuis la version 2.3.5</a><br>2.4.0 - Sera complètement supprimé</td>
<td style="width: 226.364px;">Demandez à votre fournisseur de paiement quelle solution il recommande de respecter les exigences du PSD2.</td>
</tr>
<tr>
<td style="width: 225.455px;">Authorize.net</td>
<td style="width: 226.364px;">2.3.x - <a href="https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html?lang=en#recommended-solutions">Obsolète depuis la version 2.3.4</a><br>2.4.0 - Sera complètement supprimé</td>
<td style="width: 226.364px;">Utilisez l’ <a href="https://marketplace.magento.com/authorizenet-magento-module-authorizenet.html">extension officielle</a> de Commerce Marketplace à la place.</td>
</tr>
<tr>
<td style="width: 225.455px;">Authorize.net (Direct Post)</td>
<td style="width: 226.364px;">2.3.x - <a href="https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html?lang=en#recommended-solutions">Obsolète depuis la version 2.3.1</a><br>2.4.0 - Sera complètement supprimé</td>
<td style="width: 226.364px;">Utilisez l’ <a href="https://marketplace.magento.com/authorizenet-magento-module-authorizenet.html">extension officielle</a> de Commerce Marketplace à la place.</td>
</tr>
<tr>
<td style="width: 225.455px;">CyberSource</td>
<td style="width: 226.364px;">2.3.x - <a href="https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html?lang=en#recommended-solutions">Obsolète depuis la version 2.3.3</a><br>2.4.0 - Sera complètement supprimé</td>
<td style="width: 226.364px;">Utilisez l’ <a href="https://marketplace.magento.com/cybersource-global-payment-management.html">extension officielle</a> de Commerce Marketplace à la place.</td>
</tr>
<tr>
<td style="width: 225.455px;">eWay</td>
<td style="width: 226.364px;">2.3.x - <a href="https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html?lang=en#recommended-solutions">Obsolète depuis la version 2.3.3</a><br>2.4.0 - Sera complètement supprimé</td>
<td style="width: 226.364px;">Demandez à votre fournisseur de paiement quelle solution il recommande de respecter les exigences du PSD2.</td>
</tr>
</tbody>
</table>

**Notez que l’intégration du mode de paiement principal PayPal ne sera pas obsolète ni supprimée et reste prise en charge pour toutes les versions 2.3.x et 2.4.x.**

## Comment garantir la sécurité de vos paiements

Pour tous les déploiements Adobe Commerce et Magento Open Source qui utilisent encore des intégrations de paiement obsolètes, suivez les recommandations ci-dessous afin de vous assurer que les paiements de vos clients sont sécurisés, que les paiements ne sont pas refusés et de préparer la mise à niveau vers Adobe Commerce 2.4.0 :

* Installez et configurez l’extension officielle du mode de paiement à partir de [Commerce Marketplace](https://marketplace.magento.com/extensions/payments-security/payment-integration.html?_ga=2.108129217.2105547619.1564067043-238341041.1564067043) comme indiqué dans le tableau ci-dessus.
* Désactivez les intégrations de paiement obsolètes dans Admin (définissez l’option de configuration **Activé** sur *Non* ) afin qu’elles ne s’affichent plus sur votre vitrine en tant qu’options de paiement. Assurez-vous que toutes les nouvelles commandes sont payées par l’intégration de l’extension à la place.
* Puisque la nouvelle intégration à partir de Commerce Marketplace ne pourra pas traiter les transactions de paiement effectuées à l’aide d’une intégration de paiement obsolète, nous vous recommandons d’utiliser les deux méthodes de paiement pour une période donnée en parallèle, mais seulement pour l’achèvement de transactions déjà publiées et d’éventuels remboursements. Pour ce faire, gardez le mode de paiement obsolète désactivé, mais laissez tous les champs de configuration renseignés.
