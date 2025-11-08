# Use the official MongoDB base image
FROM mongo:6.0

# Set environment variables (same as your compose file)
ENV MONGO_INITDB_ROOT_USERNAME=${MONGO_INITDB_ROOT_USERNAME}
ENV MONGO_INITDB_ROOT_PASSWORD=${MONGO_INITDB_ROOT_PASSWORD}
ENV MONGO_INITDB_DATABASE=${MONGO_INITDB_DATABASE}

# Expose MongoDB default port
EXPOSE 27017

# (Optional) Copy custom initialization scripts, if you have any
# COPY ./initdb.d /docker-entrypoint-initdb.d/

# Default command
CMD ["mongod"]
