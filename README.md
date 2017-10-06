# IMFS-MMB_DB

It contains the following tables, followed by their datatype.

# Table1: models


CREATE TABLE `models` (
	`model_id`	INTEGER UNIQUE,
	`internal_name`	text NOT NULL UNIQUE,
	`path`	text NOT NULL,
	`description_id`	integer,
	`interest`	INTEGER,
	`inflation`	INTEGER,
	`outputgap`	INTEGER,
	`outpu`	INTEGER,
	`interest_`	INTEGER,
	`fiscal_`	INTEGER,
	FOREIGN KEY(`description_id`) REFERENCES `description`(`description_id`),
	PRIMARY KEY(`model_id`)
);



# Table2: description

CREATE TABLE `description` (
	`description_id`	INT NOT NULL,
	`ac_ref`	text NOT NULL,
	`paper_title`	text,
	`journal`	text,
	`replicants_name`	text,
	`pub_date`	text,
	`keywords`	text,
	`description`	text,
	`author1`	text,
	`author2`	TEXT,
	`author3`	TEXT,
	PRIMARY KEY(`description_id`)
);


# Table3: prules

CREATE TABLE `prules` (
	`prule_id`	INT UNIQUE,
	`internal_name`	text,
	`description_id`	int,
	`param1`	real,
	`param5`	real,
	`param6`	real,
	`param7`	real,
	`param8`	real,
	`param14`	real,
	`param32`	real,
	`param33`	real,
	PRIMARY KEY(`prule_id`)
);

# Table4: models_prules
CREATE TABLE model_prules (
 model_id integer,
 prule_id integer,
 PRIMARY KEY (model_id, prule_id),
 FOREIGN KEY (model_id) REFERENCES models (model_id) 
 ON DELETE CASCADE ON UPDATE NO ACTION,
 FOREIGN KEY ([prule_id]) REFERENCES prules (prule_id) 
 ON DELETE CASCADE ON UPDATE NO ACTION
);
