## SQL

Supongamos que tenemos el siguiente esquema de Base de Datos

* Policies
* status podrá ser activa o inactiva
* Claims
* claim_type podrá ser telemático, presencial o mixto
* Users

<img src="E-R test.png" />

Write SQL queries to extract the following information:

**1)** Número de pólizas activas

```SQL
SELECT COUNT(id)
FROM Policies
WHERE status = active;
```
<br/>


**2)** Todas las campañías activas. Una compañia está activa si al menos hay una poliza activa (company_id)

```SQL
SELECT DISTINCT company_id
FROM Policies
WHERE status = active;
```

<br/>

**3)** Número de compañías activas

```SQL
SELECT COUNT(DISTINCT company_id)
FROM Policies
WHERE status = active;
```


<br/>

**4)** Numero de siniestros por cada poliza desglosado por tipo de siniestro

```SQL
SELECT Policies.id, Claims.claim_type, COUNT(Claims.id) AS count
FROM Policies
INNER JOIN Claims ON Policies.id=Claims.policy_id
GROUP BY claim_type
ORDER BY Policies.id;
```

<img src="Q4.png" />

<br/>

**5)** Número de siniestros por compañía y por tipo de evento

```SQL
SELECT Policies.company_id, Claims.claim_type, COUNT(Claims.id) AS count
FROM Policies
INNER JOIN Claims ON Policies.id=Claims.policy_id
GROUP BY claim_type
ORDER BY company_id;
```

<img src="Q5.png" />

<br/>

**6)** ¿Cómo crearias la tabla para relacionar usuarios y polizas?

```SQL
CREATE TABLE users_policies (
  users_id bigint(20) NOT NULL,
  policies_id bigint(20) NOT NULL,
  FOREIGN KEY (users_id) REFERENCES Users (id) ON DELETE RESTRICT ON UPDATE CASCADE,
  FOREIGN KEY (policies_id) REFERENCES Policies (id) ON DELETE RESTRICT ON UPDATE CASCADE,
  PRIMARY KEY (users_id, policies_id)
);
```

**7)** Número de polizas por usuario y por estado de la poliza teniendo en cuenta que puedes usar la tabla de la relación anterior

```SQL
SELECT Policies.status, Users.id, COUNT(policies.id) AS count
FROM Policies
INNER JOIN users_policies ON Policies.id = users_policies.policies_id
INNER JOIN Users ON users_policies.users_id = Users.id
GROUP BY Users.id
ORDER BY Users.id;
```
