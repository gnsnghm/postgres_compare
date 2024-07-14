# Base image
FROM almalinux/8-base

# Install dependencies
RUN yum install -y epel-release && \
    yum install -y @postgresql:9.6

# Initialize the database
USER postgres
RUN /usr/bin/initdb -D /var/lib/pgsql/data

USER root
COPY pg_hba.conf /var/lib/pgsql/data/pg_hba.conf
COPY postgresql.conf /var/lib/pgsql/data/postgresql.conf
RUN chown postgres:postgres /var/lib/pgsql/data/pg_hba.conf /var/lib/pgsql/data/postgresql.conf
RUN chmod 600 /var/lib/pgsql/data/pg_hba.conf /var/lib/pgsql/data/postgresql.conf
USER postgres

# If you wanto to init-script, delte comment out and edit initdb.sh
# COPY initdb.sh /docker-entrypoint-initdb.d/initdb.sh

# Expose the PostgreSQL port
EXPOSE 5432

# Start PostgreSQL
CMD ["/usr/bin/postgres", "-D", "/var/lib/pgsql/data/", "-c", "config_file=/var/lib/pgsql/data/postgresql.conf"]