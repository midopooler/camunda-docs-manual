---

title: 'Get Case Instances Count'
category: 'History'

keywords: 'historic get query list'

---


Query for the number of historic case instances that fulfill the given parameters.  Takes the same
parameters as the [Get Case Instances](ref:#history-get-case-instances) method.


Method
------

GET `/history/case-instance/count`


Parameters
----------

#### Query Parameters

<table class="table table-striped">
  <tr>
    <th>Name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>caseInstanceId</td>
    <td>Filter by case instance id.</td>
  </tr>
  <tr>
    <td>caseInstanceIds</td>
    <td>Filter by case instance ids. Must be a comma-separated list of case instance ids.</td>
  </tr>
    <td>caseDefinitionId</td>
    <td>Filter by the case definition the instances run on.</td>
  </tr>
  <tr>
    <td>caseDefinitionKey</td>
    <td>Filter by the key of the case definition the instances run on.</td>
  </tr>
  <tr>
    <td>caseDefinitionKeyNotIn</td>
    <td>Exclude instances that belong to a set of case definitions. Must be a comma-separated list of case definition keys.</td>
  </tr>
  <tr>
    <td>caseDefinitionName</td>
    <td>Filter by the name of the case definition the instances run on.</td>
  </tr>
  <tr>
    <td>caseDefinitionNameLike</td>
    <td>Filter by case definition names that the parameter is a substring of.</td>
  </tr>
  <tr>
    <td>caseInstanceBusinessKey</td>
    <td>Filter by case instance business key.</td>
  </tr>
  <tr>
    <td>caseInstanceBusinessKeyLike</td>
    <td>Filter by case instance business key that the parameter is a substring of.</td>
  </tr>
  <tr>
    <td>createdBefore</td>
    <td>Restrict to instances that were created before the given date. The date must have the format <code>yyyy-MM-dd'T'HH:mm:ss</code>, e.g., <code>2013-01-23T14:42:45</code>.</td>
  </tr>
  <tr>
    <td>createdAfter</td>
    <td>Restrict to instances that were created after the given date. The date must have the format <code>yyyy-MM-dd'T'HH:mm:ss</code>, e.g., <code>2013-01-23T14:42:45</code>.</td>
  </tr>
  <tr>
    <td>closedBefore</td>
    <td>Restrict to instances that were closed before the given date. The date must have the format <code>yyyy-MM-dd'T'HH:mm:ss</code>, e.g., <code>2013-01-23T14:42:45</code>.</td>
  </tr>
  <tr>
    <td>closedAfter</td>
    <td>Restrict to instances that were closed after the given date. The date must have the format <code>yyyy-MM-dd'T'HH:mm:ss</code>, e.g., <code>2013-01-23T14:42:45</code>.</td>
  </tr>
  <tr>
    <td>createdBy</td>
    <td>Only include case instances that were created by the given user.</td>
  </tr>
  <tr>
    <td>superCaseInstanceId</td>
    <td>Restrict query to all case instances that are sub case instances of the given case instance. Takes a case instance id.</td>
  </tr>
  <tr>
    <td>subCaseInstanceId</td>
    <td>Restrict query to one case instance that has a sub case instance with the given id.</td>
  </tr>
  <tr>
    <td>active</td>
    <td>Only include active case instances. Values may be <code>true</code> or <code>false</code>.</td>
  </tr>
  <tr>
    <td>completed</td>
    <td>Only include completed case instances. Values may be <code>true</code> or <code>false</code>.</td>
  </tr>
  <tr>
    <td>terminated</td>
    <td>Only include terminated case instances. Values may be <code>true</code> or <code>false</code>.</td>
  </tr>
  <tr>
    <td>closed</td>
    <td>Only include closed case instances. Values may be <code>true</code> or <code>false</code>.</td>
  </tr>
  <tr>
    <td>notClosed</td>
    <td>Only include not closed case instances. Values may be <code>true</code> or <code>false</code>.</td>
  </tr>
  <tr>
    <td>variables</td>
    <td>Only include process instances that have/had variables with certain values.
    Variable filtering expressions are comma-separated and are structured as follows:<br/>
    A valid parameter value has the form <code>key_operator_value</code>.
    <code>key</code> is the variable name, <code>operator</code> is the comparison operator to be used and <code>value</code> the variable value.<br/>
    <strong>Note:</strong> Values are always treated as <code>String</code> objects on server side.<br/>
    <br/>
    Valid operator values are: <code>eq</code> - equal to; <code>neq</code> - not equal to; <code>gt</code> - greater than;
    <code>gteq</code> - greater than or equal to; <code>lt</code> - lower than; <code>lteq</code> - lower than or equal to;
    <code>like</code>.<br/>
    <code>key</code> and <code>value</code> may not contain underscore or comma characters.
    </td>
  </tr>
</table>


Result
------

A JSON object that contains the count as the only property.

<table class="table table-striped">
  <tr>
    <th>Name</th>
    <th>Value</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>count</td>
    <td>Number</td>
    <td>The number of matching historic case instances.</td>
  </tr>
</table>


Response codes
--------------

<table class="table table-striped">
  <tr>
    <th>Code</th>
    <th>Media type</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>200</td>
    <td>application/json</td>
    <td>Request successful.</td>
  </tr>
  <tr>
    <td>400</td>
    <td>application/json</td>
    <td>Returned if some of the query parameters are invalid. See the <a href="ref:#overview-introduction">Introduction</a> for the error response format.</td>
  </tr>
</table>


Example
-------

#### Request

GET `/history/case-instance/count?notClose=true`

#### Response

```json
{
  "count": 1
}
```