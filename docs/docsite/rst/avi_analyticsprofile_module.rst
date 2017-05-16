.. _avi_analyticsprofile:


avi_analyticsprofile - Module for setup of AnalyticsProfile Avi RESTful Object
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* This module is used to configure AnalyticsProfile object
* more examples at https://github.com/avinetworks/devops


Requirements (on host that executes module)
-------------------------------------------

  * avisdk


Options
-------

.. raw:: html

    <table border=1 cellpadding=4>
    <tr>
    <th class="head">parameter</th>
    <th class="head">required</th>
    <th class="head">default</th>
    <th class="head">choices</th>
    <th class="head">comments</th>
    </tr>
                <tr><td>apdex_response_threshold<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>If a client receives an http response in less than the satisfactory latency threshold, the request is considered satisfied.</div><div>It is considered tolerated if it is not satisfied and less than tolerated latency factor multiplied by the satisfactory latency threshold.</div><div>Greater than this number and the client's request is considered frustrated.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as 500.</div>        </td></tr>
                <tr><td>apdex_response_tolerated_factor<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Client tolerated response latency factor.</div><div>Client must receive a response within this factor times the satisfactory threshold (apdex_response_threshold) to be considered tolerated.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as 4.0.</div>        </td></tr>
                <tr><td>apdex_rtt_threshold<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Satisfactory client to avi round trip time(rtt).</div><div>Default value when not specified in API or module is interpreted by Avi Controller as 250.</div>        </td></tr>
                <tr><td>apdex_rtt_tolerated_factor<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Tolerated client to avi round trip time(rtt) factor.</div><div>It is a multiple of apdex_rtt_tolerated_factor.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as 4.0.</div>        </td></tr>
                <tr><td>apdex_rum_threshold<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>If a client is able to load a page in less than the satisfactory latency threshold, the pageload is considered satisfied.</div><div>It is considered tolerated if it is greater than satisfied but less than the tolerated latency multiplied by satisifed latency.</div><div>Greater than this number and the client's request is considered frustrated.</div><div>A pageload includes the time for dns lookup, download of all http objects, and page render time.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as 5000.</div>        </td></tr>
                <tr><td>apdex_rum_tolerated_factor<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Virtual service threshold factor for tolerated page load time (plt) as multiple of apdex_rum_threshold.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as 4.0.</div>        </td></tr>
                <tr><td>apdex_server_response_threshold<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A server http response is considered satisfied if latency is less than the satisfactory latency threshold.</div><div>The response is considered tolerated when it is greater than satisfied but less than the tolerated latency factor * s_latency.</div><div>Greater than this number and the server response is considered frustrated.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as 400.</div>        </td></tr>
                <tr><td>apdex_server_response_tolerated_factor<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Server tolerated response latency factor.</div><div>Servermust response within this factor times the satisfactory threshold (apdex_server_response_threshold) to be considered tolerated.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as 4.0.</div>        </td></tr>
                <tr><td>apdex_server_rtt_threshold<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Satisfactory client to avi round trip time(rtt).</div><div>Default value when not specified in API or module is interpreted by Avi Controller as 125.</div>        </td></tr>
                <tr><td>apdex_server_rtt_tolerated_factor<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Tolerated client to avi round trip time(rtt) factor.</div><div>It is a multiple of apdex_rtt_tolerated_factor.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as 4.0.</div>        </td></tr>
                <tr><td>client_log_config<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Clientlogconfiguration settings for analyticsprofile.</div>        </td></tr>
                <tr><td>conn_lossy_ooo_threshold<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A connection between client and avi is considered lossy when more than this percentage of out of order packets are received.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as 50.</div>        </td></tr>
                <tr><td>conn_lossy_timeo_rexmt_threshold<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A connection between client and avi is considered lossy when more than this percentage of packets are retransmitted due to timeout.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as 20.</div>        </td></tr>
                <tr><td>conn_lossy_total_rexmt_threshold<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A connection between client and avi is considered lossy when more than this percentage of packets are retransmitted.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as 50.</div>        </td></tr>
                <tr><td>conn_lossy_zero_win_size_event_threshold<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A client connection is considered lossy when percentage of times a packet could not be trasmitted due to tcp zero window is above this threshold.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as 2.</div>        </td></tr>
                <tr><td>conn_server_lossy_ooo_threshold<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A connection between avi and server is considered lossy when more than this percentage of out of order packets are received.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as 50.</div>        </td></tr>
                <tr><td>conn_server_lossy_timeo_rexmt_threshold<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A connection between avi and server is considered lossy when more than this percentage of packets are retransmitted due to timeout.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as 20.</div>        </td></tr>
                <tr><td>conn_server_lossy_total_rexmt_threshold<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A connection between avi and server is considered lossy when more than this percentage of packets are retransmitted.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as 50.</div>        </td></tr>
                <tr><td>conn_server_lossy_zero_win_size_event_threshold<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A server connection is considered lossy when percentage of times a packet could not be trasmitted due to tcp zero window is above this threshold.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as 2.</div>        </td></tr>
                <tr><td>controller<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>IP address or hostname of the controller. The default value is the environment variable <code>AVI_CONTROLLER</code>.</div>        </td></tr>
                <tr><td>description<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>User defined description for the object.</div>        </td></tr>
                <tr><td>disable_se_analytics<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Disable node (service engine) level analytics forvs metrics.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as False.</div>        </td></tr>
                <tr><td>disable_server_analytics<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Disable analytics on backend servers.</div><div>This may be desired in container environment when there are large number of  ephemeral servers.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as False.</div>        </td></tr>
                <tr><td>exclude_client_close_before_request_as_error<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Exclude client closed connection before an http request could be completed from being classified as an error.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as False.</div>        </td></tr>
                <tr><td>exclude_gs_down_as_error<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Exclude queries to gslb services that are operationally down from the list of errors.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as False.</div>        </td></tr>
                <tr><td>exclude_http_error_codes<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>List of http status codes to be excluded from being classified as an error.</div><div>Error connections or responses impacts health score, are included as significant logs, and may be classified as part of a dos attack.</div>        </td></tr>
                <tr><td>exclude_invalid_dns_domain_as_error<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Exclude dns queries to domains outside the domains configured in the dns application profile from the list of errors.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as False.</div>        </td></tr>
                <tr><td>exclude_invalid_dns_query_as_error<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Exclude invalid dns queries from the list of errors.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as False.</div>        </td></tr>
                <tr><td>exclude_no_dns_record_as_error<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Exclude queries to domains that did not have configured services/records from the list of errors.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as False.</div>        </td></tr>
                <tr><td>exclude_no_valid_gs_member_as_error<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Exclude queries to gslb services that have no available members from the list of errors.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as False.</div>        </td></tr>
                <tr><td>exclude_persistence_change_as_error<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Exclude persistence server changed while load balancing' from the list of errors.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as False.</div>        </td></tr>
                <tr><td>exclude_server_dns_error_as_error<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Exclude server dns error response from the list of errors.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as False.</div>        </td></tr>
                <tr><td>exclude_server_tcp_reset_as_error<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Exclude server tcp reset from errors.</div><div>It is common for applications like ms exchange.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as False.</div>        </td></tr>
                <tr><td>exclude_syn_retransmit_as_error<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Exclude 'server unanswered syns' from the list of errors.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as False.</div>        </td></tr>
                <tr><td>exclude_tcp_reset_as_error<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Exclude tcp resets by client from the list of potential errors.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as False.</div>        </td></tr>
                <tr><td>exclude_unsupported_dns_query_as_error<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Exclude unsupported dns queries from the list of errors.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as False.</div>        </td></tr>
                <tr><td>hs_event_throttle_window<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Time window (in secs) within which only unique health change events should occur.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as 1209600.</div>        </td></tr>
                <tr><td>hs_max_anomaly_penalty<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Maximum penalty that may be deducted from health score for anomalies.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as 10.</div>        </td></tr>
                <tr><td>hs_max_resources_penalty<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Maximum penalty that may be deducted from health score for high resource utilization.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as 25.</div>        </td></tr>
                <tr><td>hs_max_security_penalty<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Maximum penalty that may be deducted from health score based on security assessment.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as 100.</div>        </td></tr>
                <tr><td>hs_min_dos_rate<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Dos connection rate below which the dos security assessment will not kick in.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as 1000.</div>        </td></tr>
                <tr><td>hs_performance_boost<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Adds free performance score credits to health score.</div><div>It can be used for compensating health score for known slow applications.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as 0.</div>        </td></tr>
                <tr><td>hs_pscore_traffic_threshold_l4_client<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Threshold number of connections in 5min, below which apdexr, apdexc, rum_apdex, and other network quality metrics are not computed.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as 10.0.</div>        </td></tr>
                <tr><td>hs_pscore_traffic_threshold_l4_server<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Threshold number of connections in 5min, below which apdexr, apdexc, rum_apdex, and other network quality metrics are not computed.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as 10.0.</div>        </td></tr>
                <tr><td>hs_security_certscore_expired<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Score assigned when the certificate has expired.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as 0.0.</div>        </td></tr>
                <tr><td>hs_security_certscore_gt30d<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Score assigned when the certificate expires in more than 30 days.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as 5.0.</div>        </td></tr>
                <tr><td>hs_security_certscore_le07d<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Score assigned when the certificate expires in less than or equal to 7 days.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as 2.0.</div>        </td></tr>
                <tr><td>hs_security_certscore_le30d<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Score assigned when the certificate expires in less than or equal to 30 days.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as 4.0.</div>        </td></tr>
                <tr><td>hs_security_chain_invalidity_penalty<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Penalty for allowing certificates with invalid chain.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as 1.0.</div>        </td></tr>
                <tr><td>hs_security_cipherscore_eq000b<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Score assigned when the minimum cipher strength is 0 bits.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as 0.0.</div>        </td></tr>
                <tr><td>hs_security_cipherscore_ge128b<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Score assigned when the minimum cipher strength is greater than equal to 128 bits.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as 5.0.</div>        </td></tr>
                <tr><td>hs_security_cipherscore_lt128b<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Score assigned when the minimum cipher strength is less than 128 bits.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as 3.5.</div>        </td></tr>
                <tr><td>hs_security_encalgo_score_none<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Score assigned when no algorithm is used for encryption.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as 0.0.</div>        </td></tr>
                <tr><td>hs_security_encalgo_score_rc4<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Score assigned when rc4 algorithm is used for encryption.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as 2.5.</div>        </td></tr>
                <tr><td>hs_security_hsts_penalty<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Penalty for not enabling hsts.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as 1.0.</div>        </td></tr>
                <tr><td>hs_security_nonpfs_penalty<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Penalty for allowing non-pfs handshakes.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as 1.0.</div>        </td></tr>
                <tr><td>hs_security_selfsignedcert_penalty<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Deprecated.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as 1.0.</div>        </td></tr>
                <tr><td>hs_security_ssl30_score<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Score assigned when supporting ssl3.0 encryption protocol.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as 3.5.</div>        </td></tr>
                <tr><td>hs_security_tls10_score<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Score assigned when supporting tls1.0 encryption protocol.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as 5.0.</div>        </td></tr>
                <tr><td>hs_security_tls11_score<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Score assigned when supporting tls1.1 encryption protocol.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as 5.0.</div>        </td></tr>
                <tr><td>hs_security_tls12_score<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Score assigned when supporting tls1.2 encryption protocol.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as 5.0.</div>        </td></tr>
                <tr><td>hs_security_weak_signature_algo_penalty<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Penalty for allowing weak signature algorithm(s).</div><div>Default value when not specified in API or module is interpreted by Avi Controller as 1.0.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The name of the analytics profile.</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Password of Avi user in Avi controller. The default value is the environment variable <code>AVI_PASSWORD</code>.</div>        </td></tr>
                <tr><td>ranges<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>List of http status code ranges to be excluded from being classified as an error.</div>        </td></tr>
                <tr><td>resp_code_block<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Block of http response codes to be excluded from being classified as an error.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>absent</li><li>present</li></ul></td>
        <td><div>The state that should be applied on the entity.</div>        </td></tr>
                <tr><td>tenant<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>admin</td>
        <td></td>
        <td><div>Name of tenant used for all Avi API calls and context of object.</div>        </td></tr>
                <tr><td>tenant_ref<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>It is a reference to an object of type tenant.</div>        </td></tr>
                <tr><td>tenant_uuid<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>UUID of tenant used for all Avi API calls and context of object.</div>        </td></tr>
                <tr><td>url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Avi controller URL of the object.</div>        </td></tr>
                <tr><td>username<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Username used for accessing Avi controller. The default value is the environment variable <code>AVI_USERNAME</code>.</div>        </td></tr>
                <tr><td>uuid<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Uuid of the analytics profile.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

      - name: Create a custom Analytics profile object
        avi_analyticsprofile:
          controller: ''
          username: ''
          password: ''
          apdex_response_threshold: 500
          apdex_response_tolerated_factor: 4.0
          apdex_rtt_threshold: 250
          apdex_rtt_tolerated_factor: 4.0
          apdex_rum_threshold: 5000
          apdex_rum_tolerated_factor: 4.0
          apdex_server_response_threshold: 400
          apdex_server_response_tolerated_factor: 4.0
          apdex_server_rtt_threshold: 125
          apdex_server_rtt_tolerated_factor: 4.0
          conn_lossy_ooo_threshold: 50
          conn_lossy_timeo_rexmt_threshold: 20
          conn_lossy_total_rexmt_threshold: 50
          conn_lossy_zero_win_size_event_threshold: 2
          conn_server_lossy_ooo_threshold: 50
          conn_server_lossy_timeo_rexmt_threshold: 20
          conn_server_lossy_total_rexmt_threshold: 50
          conn_server_lossy_zero_win_size_event_threshold: 2
          disable_se_analytics: false
          disable_server_analytics: false
          exclude_client_close_before_request_as_error: false
          exclude_persistence_change_as_error: false
          exclude_server_tcp_reset_as_error: false
          exclude_syn_retransmit_as_error: false
          exclude_tcp_reset_as_error: false
          hs_event_throttle_window: 1209600
          hs_max_anomaly_penalty: 10
          hs_max_resources_penalty: 25
          hs_max_security_penalty: 100
          hs_min_dos_rate: 1000
          hs_performance_boost: 20
          hs_pscore_traffic_threshold_l4_client: 10.0
          hs_pscore_traffic_threshold_l4_server: 10.0
          hs_security_certscore_expired: 0.0
          hs_security_certscore_gt30d: 5.0
          hs_security_certscore_le07d: 2.0
          hs_security_certscore_le30d: 4.0
          hs_security_chain_invalidity_penalty: 1.0
          hs_security_cipherscore_eq000b: 0.0
          hs_security_cipherscore_ge128b: 5.0
          hs_security_cipherscore_lt128b: 3.5
          hs_security_encalgo_score_none: 0.0
          hs_security_encalgo_score_rc4: 2.5
          hs_security_hsts_penalty: 0.0
          hs_security_nonpfs_penalty: 1.0
          hs_security_selfsignedcert_penalty: 1.0
          hs_security_ssl30_score: 3.5
          hs_security_tls10_score: 5.0
          hs_security_tls11_score: 5.0
          hs_security_tls12_score: 5.0
          hs_security_weak_signature_algo_penalty: 1.0
          name: jason-analytics-profile
          tenant_ref: Demo

Return Values
-------------

Common return values are documented here :doc:`common_return_values`, the following are the fields unique to this module:

.. raw:: html

    <table border=1 cellpadding=4>
    <tr>
    <th class="head">name</th>
    <th class="head">description</th>
    <th class="head">returned</th>
    <th class="head">type</th>
    <th class="head">sample</th>
    </tr>

        <tr>
        <td> obj </td>
        <td> AnalyticsProfile (api/analyticsprofile) object </td>
        <td align=center> success, changed </td>
        <td align=center> dict </td>
        <td align=center>  </td>
    </tr>
        
    </table>
    </br></br>




Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
