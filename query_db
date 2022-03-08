SELECT 
    #posts.ID AS p,
    CONCAT('<a href="https://distripharmalink.com/store/',users.user_nicename,'/?table_filter=',users.user_nicename,'">',users.user_nicename,'</a>') AS  `SupplierCompanyName`,#company Name#
    #users.user_nicename `Supplier Company Name`,
	#SUBSTRING(SUBSTRING(SUBSTRING(usermeta.meta_value,LOCATE('city',usermeta.meta_value)+7),LOCATE('"',SUBSTRING(usermeta.meta_value,LOCATE('city',usermeta.meta_value)+7))+1),1,LOCATE('"',SUBSTRING(SUBSTRING(usermeta.meta_value,LOCATE('city',usermeta.meta_value)+7),LOCATE('"',SUBSTRING(usermeta.meta_value,LOCATE('city',usermeta.meta_value)+7))+1))-1) City,#city#
	#SUBSTRING(SUBSTRING(SUBSTRING(usermeta.meta_value,LOCATE('phone',usermeta.meta_value)+7),LOCATE('"',SUBSTRING(usermeta.meta_value,LOCATE('phone',usermeta.meta_value)+7))+1),1,LOCATE('"',SUBSTRING(SUBSTRING(usermeta.meta_value,LOCATE('phone',usermeta.meta_value)+7),LOCATE('"',SUBSTRING(usermeta.meta_value,LOCATE('phone',usermeta.meta_value)+7))+1))-1)  AS `Supplier Phone`,#phone#
    #users.user_email `Supplier Email`
    
FROM `wp_posts` posts,`wp_usermeta` usermeta,`wp_postmeta` postmeta,`wp_postmeta` postmeta1,`wp_postmeta` postmeta2,`wp_term_relationships` term_relationships,`wp_term_taxonomy` term_taxonomy,`wp_terms` terms,wp_users users
WHERE posts.post_author=usermeta.user_id 
	AND posts.post_type='product' 
	AND usermeta.meta_key='dokan_profile_settings'
	AND posts.post_status='publish'
	AND postmeta.post_id=posts.ID #attention#
	AND term_relationships.object_id=posts.ID
	AND term_taxonomy.term_taxonomy_id=term_relationships.term_taxonomy_id
	AND term_relationships.term_taxonomy_id!=2 #attention#
	AND term_taxonomy.term_id=terms.term_id 
	AND term_taxonomy.taxonomy='product_cat' #attention#
    
    #AND postmeta.post_id=posts.ID#
	AND postmeta1.post_id=posts.ID
	AND postmeta2.post_id=posts.ID
    
	AND postmeta.meta_key='_price'
	AND postmeta1.meta_key="_stock_status"
	AND postmeta2.meta_key="_stock"
	AND postmeta1.meta_value="instock"
	AND users.ID=usermeta.user_id
    GROUP BY `SupplierCompanyName`
