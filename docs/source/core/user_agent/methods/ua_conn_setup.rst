..
  Most of our documentation is generated from our source code comments,
    please head to github.com/cee-studio/orca if you want to contribute!

  The following files contains the documentation used to generate this page: 
  - common/user-agent.h

=======================================
ua_conn_setup - set transfer attributes
=======================================

.. doxygenfunction:: ua_conn_setup

Example
-------

.. code:: c

   struct user_agent *ua = ua_init(NULL); 
   ua_set_url(ua, "https://www.example.com");

   struct sized_buffer body = { "hi", 2 };
   struct ua_conn_attr conn_attr = { .method = HTTP_POST,
                                     .body = &body,
                                     .endpoint = "/echo?m=POST" };
   struct ua_conn *conn = ua_conn_start(ua);
   ua_conn_setup(conn, &conn_attr);

   ua_conn_easy_perform(conn);

   ua_conn_stop(conn);
   ua_cleanup(ua);
